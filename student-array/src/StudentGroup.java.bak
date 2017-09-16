import java.util.ArrayList;
import java.util.Arrays;
import java.util.Calendar;
import java.util.Date;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class StudentGroup implements GroupOperationService {

	private Student[] students;
	
	public StudentGroup(int length) {
        students = new Student[0];
	}

	@Override
	public Student[] getStudents() {
         return this.students;
	}

	@Override
	public void setStudents(Student[] students) {
         this.students = students;
	}

	@Override
	public Student getStudent(int index) {
          return students[index];
	}

	@Override
	public void setStudent(Student student, int index) {
           
this.getStudents()[index] = student;
	}
	@Override
	public void addFirst(Student student) {
         Student[] temp = new Student[this.students.length+1];
		 temp[0] = student;
		 for(int i = 1; i < temp.length; i++)
			 temp[i] = this.students[i-1];
		 this.students = temp;
	}

	@Override
	public void addLast(Student student) {
         Student[] temp = new Student[this.getStudents().length+1];
		 for(int i = 0; i < this.students.length; i++)
			 temp[i] = this.students[i];
		 temp[temp.length - 1] = student;
		 this.students = temp;
	}

	@Override
	public void remove(int index) {
         Student[] temp = new Student[this.students.length-1]; 
		 int c = 0;
		 for(int i = 0; i < this.students.length; i++)
			 if(i != index) temp[c++] = this.students[i];
		 this.students = temp;
	}

	@Override
	public void remove(Student student) {
         Student[] temp = new Student[this.students.length-1]; 
		 int c = 0;
		 for(int i = 0; i < this.students.length; i++)
			 if(this.students[i] != student) temp[c++] = this.students[i];
		 this.students = temp;
	}

	@Override
	public void removeFromIndex(int index) {
         Student[] temp = new Student[index]; 
		 int c = 0;
		 for(int i = 0; i < index; i++)
			 temp[i] = this.students[i];
		 this.students = temp; 
	}

	@Override
	public void removeFromElement(Student student) {
           int ind = getStudentIndex(student);
		   ArrayList<Student> temp = new ArrayList<>();
		   for(int i = 0; i < ind; i++)
			   temp.add(this.students[i]);
		   this.students = temp.toArray(new Student[temp.size()]);
	}

	@Override
	public void removeToIndex(int index) {
         Student[] temp = new Student[this.students.length-index]; 
		 int c = 0;
		 for(int i = index; i < this.students.length; i++)
			 temp[i-index] = this.students[i];
		 this.students = temp;
	}

	@Override
	public void removeToElement(Student student) {
           int ind = getStudentIndex(student);
		   ArrayList<Student> temp = new ArrayList<>();
		   for(int i = ind; i < this.students.length; i++)
			   temp.add(this.students[i]);
		   this.students = temp.toArray(new Student[temp.size()]);
	}

	@Override
	public void bubbleSort() {
          for(int i = 0; i < this.students.length; i++)
		  {
			  
	          for(int j = 0; j < this.students.length-i-1; j++)
			  {
                   if(this.students[j].getId() > this.students[j+1].getId())
				   {
					   Student temp = this.students[j];
					   this.students[j] = this.students[j+1];
					   this.students[j+1] = temp;
				   }
			  }	   
		  }
	}

	@Override
	public Student[] getByBirthDate(Date date) {
           ArrayList<Student> temp1 = new ArrayList<>();
		   for(Student s : this.students)
		   {
		       if(s.getBirthDate().compareTo(date) == 0)
				   temp1.add(s);
		   }
		   return  temp1.toArray(new Student[temp1.size()]);
	}

	@Override
	public Student[] getBetweenBirthDates(Date firstDate, Date lastDate) {
         ArrayList<Student> temp1= new ArrayList<>();
		   for(Student s : this.students)
		   {
		       if(s.getBirthDate().after(firstDate) && s.getBirthDate().before(lastDate))
				   temp1.add(s);
		   }
		   return  temp1.toArray(new Student[temp1.size()]); 
	}

	@Override
	public Student[] getNearBirthDate(Date date, int days) {
           ArrayList<Student> temp1 = new ArrayList<>();
		   Calendar cal = getCalendar(date);
		   cal.add(Calendar.DATE, days);
           date = cal.getTime();
		   for(Student s : this.students)
		   {
		       if(s.getBirthDate().before(date))
				   temp1.add(s);
		   }
		   return  temp.toArray(new Student[temp.size()]); 
	}

	@Override
	public int getCurrentAgeByDate(int indexOfStudent) {
		   Date now = new Date();
           return this.students[indexOfStudent].getBirthDate().getYear() - now.getYear();
	}

	@Override
	public Student[] getStudentsByAge(int age) {
          ArrayList<Student> temp = new ArrayList<>();
		  for(int j = 0; j < this.students.length; j++)
		  {
		      if(getCurrentAgeByDate(i) == age)
				  temp.add(this.students[j]);
		  }
          return  temp.toArray(new Student[temp.size()]);
	}

	@Override
	public Student[] getStudentsWithMaxAvgMark() {
          double maxavg = 0;
		  for(Student s : this.students)
			  if(s.getAvgMark() > maxavg) maxavg = s.getAvgMark();
		  ArrayList<Student> temp1 = new ArrayList<>();
		  for(Student s : this.students)
			  if(s.getAvgMark() == maxavg)  temp1.add(s);
		  return  temp1.toArray(new Student[temp1.size()]);
	}

	@Override
	public Student getNextStudent(Student student) {
           this.bubbleSort();
		   int j;
		   for(j = 0; j < this.students.length; j++)
			   if(this.students[j].equals(student)) break;
		   return this.students[j+1];

	}

	@Override
	public void add(Student student, int index) {
         Student[] temp1 = new Student[this.students.length+1];
		 for(int j = 0; j < index; j++)
			 temp1[j] = this.students[j];
		 temp1[index] = student;
		 for(int j = index; j < this.students.length; j++)
			 temp1[j+1] = this.students[j];
		 this.students = temp1;
	}

	private int getStudentIndex(Student student) {
         for(int j = 0; j < this.students.length; j++)
			 if(this.students[j].equals(student)) return j;
		 return -1;
    }

	private int getDiffYears(Date first, Date last) {
            return first.getYear() - last.getYear();
	}

	private Calendar getCalendar(Date date) {
          Calendar aDay = Calendar.getInstance();
          aDay.setTime(date);
		  return aDay;
	}

}