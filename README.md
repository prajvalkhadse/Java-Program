# Java-Program
Age calculator
import java.util.Calendar;//it is array in month it will print 0 for jan
import java.time.LocalDate;//onwards java 8
import java.lang.Exception;
class InvalidBirthdateException extends Exception{
	String msg;
      InvalidBirthdateException(String s){
		msg=s;
      }
	  public String toString(){
	  return("InvalidBirthdateException"+ msg);
	  }
}
class Practical10c{
	public static void main(String[] args){
		 int Date=Integer.parseInt(args[0]);
         int Month=Integer.parseInt(args[1]);
         int Year=Integer.parseInt(args[2]);
		 LocalDate CDate=LocalDate.now();//getting current date in yy/mm/dd format
		 int day = CDate.getDayOfMonth();//for getting today's date form month
		 

		 Calendar calen = Calendar.getInstance();
			int mont;
			mont=CDate.getMonthValue();//mont is month

		 int y = CDate.getYear();//y is year for current year

		 System.out.println("Current date is : "+day+"/"+mont+"/"+y);
		 System.out.println("Your Birth date is : "+Date+"/"+Month+"/"+Year);
         int CYear=y-Year;
		 int CMonth=mont-Month;
		 
		 try{
			 if (Date==0 || Month==0 || Year==0){
				 throw new InvalidBirthdateException(":-- "+"Birhdate can't be zero"); 
			 }
		 }catch(InvalidBirthdateException e){
			 System.out.println(e );
		 }
		
         try{
			 if(Month==0 || Month>12){
				 throw new InvalidBirthdateException("Invalid month");
			 }
		if(Month==1 && Date>31 || Month==3 && Date>31 || Month==5 && Date>31 || Month==7 && Date>31 || Month==8 && Date>31 || Month==10 && Date>31 || Month==12 && Date>31){
				throw new InvalidBirthdateException(":-- "+"For month 1,3,5,7,8,10 and 12 date should be between 1 to 31");	
		}
		
		if(Month==4 && Date>=30 | Month==6 && Date>=30 | Month==8 && Date>=30 | Month==9 && Date>=30 | Month==8 && Date>=30 | Month==10 && Date>=31 | Month==11 && Date>=30){
				throw new InvalidBirthdateException(":-- "+"For month 4,6,8,9 and 11 date should be between 1 to 30");	
		}
		if(Month==2 && ((Year%4==0) && (Year%100!=0)) || (Year%400==0)){
				if(Date>29){
					throw new InvalidBirthdateException(":-- "+"If leap year then date upto 29");
				}
		}
		
		else if(Month==2 && Date>28){
			throw new InvalidBirthdateException("Date should be upto 28");
		}
		 
		
		 if (Year>y || mont>Month && Month>mont){
                throw new InvalidBirthdateException(":-- "+"year or month is greater than current year"); 
			 }
			 System.out.println("Your Age is "+ CYear);
		}
		 catch(InvalidBirthdateException e){
			 System.out.println(e);
			 //System.out.println("Your Age is "+ CYear);

		 }
		
	}
}
 	
 
