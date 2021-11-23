1)))))))))))))))))))))))))))))))))))))))))))))
package manoj;
import java.sql.*;
public class Department {
public static void main(String[] args) {
		
		Statement st,st2;
		ResultSet rs,rs2;
		Connection con;
		
		String driver="com.mysql.jdbc.Driver";
		String url="jdbc:mysql://localhost:3306/";
		String dbname="department";
		String username="root";
		String password="";
		
		try{
			Class.forName(driver);
			con=DriverManager.getConnection(url+dbname,username,password);
			String q1="select No_of_Employee from department where Name='CSE'";
			st=con.createStatement();
			rs=st.executeQuery(q1);
			while(rs.next())
			{
				int no=rs.getInt("No_of_Employee");
				System.out.println("No of employees = "+no);
				
			}
			
			st2=con.createStatement();
			String q2="select Name,Dept_id from department where Year_Established ='1970'";
			rs2=st2.executeQuery(q2);
			while(rs2.next())
			{
				String name=rs2.getString("Name");
				int did=rs2.getInt("Dept_id");
				System.out.println("Name : "+name+" Did: "+did);
				
			}
			st.close();
			st2.close();
			con.close();
		}
		catch(Exception e)
		{
			System.out.print(e);
		}
	
	}

}
 2)))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))
 package student;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class Student {
	public static void main (String args[]) {
		String driver="com.mysql.jdbc.Driver";
		String url="jdbc:mysql://localhost:3306/";
		String dbname="college";
		String username="root";
		String password="";
		Connection con;
		try {
			Class.forName(driver);
			con=DriverManager.getConnection(url+dbname,username,password);
			String query1 = "SELECT * FROM `Student` WHERE cgpa < 9";
			String query3 = "Select * from Student";
			Statement st = con.createStatement();
			ResultSet rs = st.executeQuery(query1);
			while(rs.next()) {
				int usn = rs.getInt(1);
				String name = rs.getString(2);
				double cgpa = rs.getDouble(3);
				System.out.println("USN, NAME, CGPA : " + usn + ", " + name + ", " + cgpa);
			}
			
			st = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);
			rs = st.executeQuery(query3);
			System.out.println("Updated");
			while(rs.next()) {
				if(rs.getString(2).equals("John")){
					rs.updateDouble(3, 8.9);
					rs.updateRow();
				}
				int usn = rs.getInt(1);
				String name = rs.getString(2);
				double cgpa = rs.getDouble(3);
				System.out.println("USN, NAME, CGPA : " + usn + ", " + name + ", " + cgpa);
				
			}
						
			
		} catch(Exception e) {
			e.printStackTrace();
		}
	
	}
}

4))))))))))))))))))))))))))))))))))))))))))))))))))))))))
<!----------------------html------------------------>


<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<form action = "q5" method = "post">
		<input type="text" placeholder = "Enter full name" name = "fullName">
		<input type="submit">
	</form>
</body>
</html>







---------------------------------------------------------------

Servlet


import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


/**
 * Servlet implementation class q5
 */
@WebServlet("/q5")
public class q5 extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public q5() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
//		doGet(request, response);
		String fullName = request.getParameter("fullName");
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		String name = initials(fullName);
		out.println(name);
		
	}
	private String initials(String fullName) {
		String[] name = fullName.trim().split("\s");
		String initial = "" ;
		for(String i : name) {
//			initial += String.valueOf(i.charAt(0));
			initial += i.charAt(0);
		}		
		return initial.toUpperCase();
	}
}
5))))))))))))))))))))))))))))))))))))))))))))))))))))
servelet
-----------------------------------------

import java.io.IOException;
import java.io.PrintWriter;
//import java.sql.Connection;
//import java.sql.Date;
//import java.sql.PreparedStatement;
//import java.sql.ResultSet;
//import java.sql.Driver;
import java.sql.*;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;





/**
 * Servlet implementation class Q6
 */
@WebServlet("/Q6")
public class Q6 extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Q6() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
//		doGet(request, response);
		int emp_id = Integer.parseInt(request.getParameter("emp_id"));
		String emp_name = request.getParameter("emp_name");
		String address = request.getParameter("address");
		Date dob = Date.valueOf(request.getParameter("dob"));
		response.setContentType("text/html");
		String dbDriver = "com.mysql.jdbc.Driver";
		String dbURL = "jdbc:mysql://localhost:3306/1ms19cs068";
		String dbUser = "root";
		String dbPass = "";
		Connection con;
		try {
			Class.forName(dbDriver);
			con = DriverManager.getConnection(dbURL, dbUser, dbPass);
			String query1 = "INSERT INTO `Employee` (`emp_id`, `emp_name`, `address`, `dob`) VALUES (?, ?, ?, ?) ";
			PreparedStatement ps = con.prepareStatement(query1);
			ps.setInt(1, emp_id);
			ps.setString(2, emp_name);
			ps.setString(3, address);
			ps.setDate(4, dob);
			ps.execute();
		
			String query2 = "SELECT * FROM Employee";
			
			ResultSet rs = ps.executeQuery(query2);
			PrintWriter out = response.getWriter();
			while(rs.next()) {
				emp_id = rs.getInt(1);
				emp_name = rs.getString(2);
				address = rs.getString(3);
				dob = rs.getDate(4);
				String fin = "<h2>Empid, Emp Name, Address, dob : " + emp_id +", " + emp_name + ", " + address + ", " + String.valueOf(dob) + "</h2><br>";
				out.println(fin);
			}
			
			
		} catch(Exception e) {
			e.printStackTrace();
		}
		
	}

}



------------------------------------------------------------


html




<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<form action="Q6" method="post">
		<input type= "text" placeholder = "Emp ID" name="emp_id">
		<input type= "text" placeholder = "Emp Name" name="emp_name">
		<input type= "text" placeholder = "Address" name="address">
		<input type= "date" placeholder = "DOB" name="dob">
		
		<input type="submit" value="Insert">
	</form>
</body>
</html>
7))))))))))))))))))))))))))))))))))))))))))))))))
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	
	<form action="a.jsp" method = "post">
		<input type = "text" placeholder = "name" name = "name">
		<input type = "number" placeholder = "age" name = "age" >
		<input type = "submit" name = "submit_btn">
	</form>

	<%
		if(request.getParameter("submit_btn") != null){
			int price;
			String name = request.getParameter("name");
			int age = Integer.parseInt(request.getParameter("age"));
			if(age > 62){
				price = 50;
			} else if(age < 10){
				price = 30;
			} else{
				price = 80;
			}
			out.print("Name : " + name + ", Age: " + age + ", Price: " + price);
			
			
		}
	
	%>
	
</body>
</html>
  8)))))))))))))))))))))))))))))))))))))))))))))
  insert.jsp
------------------------------------------------



<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>

	<%@ page import = "java.sql.* "  %>
	
	<form name = "insert_data" action = "ins.jsp" method = "POST">
		<input type = "text" name = "bookno" placeholder = "bookno">
		<input type = "text" name = "title" placeholder = "title">
		<input type = "text" name = "author" placeholder = "author">
		<input type = "text" name = "publication" placeholder = "publication">
		<input type = "text" name = "price" placeholder = "price">
		
		<input type = "submit" value = "insert" name = "insert">
		
	</form>
	
	
	<%	String dbURL = "jdbc:mysql://localhost:3306/";
		String dbName = "library";
		String dbDriver = "com.mysql.jdbc.Driver";
		String dbUsername = "root";
		String dbPass = "";

		Class.forName(dbDriver);

		Connection con = null;
		if(request.getParameter("insert") != null){
			try{
				con = DriverManager.getConnection(dbURL + dbName, dbUsername, dbPass);
				int bookno = Integer.parseInt(request.getParameter("bookno"));
				String title = request.getParameter("title");
				String author = request.getParameter("author");
				String publication = request.getParameter("publication");
				int price = Integer.parseInt(request.getParameter("price"));
				
				String query = "INSERT INTO BookDetails VALUES (?, ?, ?, ?, ?)";
				
				PreparedStatement ps = con.prepareStatement(query);
				ps.setInt(1,bookno );
				ps.setString(2, title);			
				ps.setString(3, author);			
				ps.setString(4, publication);			
				ps.setInt(5, price);
				ps.execute();
				ps.close();
				out.println("Inserted book Successfully..");
			} catch(Exception e){
				e.printStackTrace();
			}
						
		}
		
	%>



</body>
</html>




---------------------------------------------------------

retrieve.jsp



<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>

	<%@ page import = "java.sql.* "  %>
	
	<form name = "retrieve" action = "aut.jsp" method = "POST">
		<input type = "text" name = "title" placeholder = "title">
		
		<input type = "submit" value = "retrieve" name = "retrieve">
		
	</form>
	
	<%	
		String dbURL = "jdbc:mysql://localhost:3306/";
		String dbName = "library";
		String dbDriver = "com.mysql.jdbc.Driver";
		String dbUsername = "root";
		String dbPass = "";
	
		Class.forName(dbDriver);
	
		Connection con;
	
	
		
		if(request.getParameter("retrieve") != null){
			try{
				
				con = DriverManager.getConnection(dbURL + dbName, dbUsername, dbPass);
				
				String title = request.getParameter("title");
				
				String query = "SELECT * FROM BookDetails WHERE title = ?";
				

				PreparedStatement st = con.prepareStatement(query);
				st.setString(1, title);
				ResultSet rs = st.executeQuery();
				while(rs.next()){
					int bookno = rs.getInt(1);
					String author = rs.getString(3);
					String publication = rs.getString(4);
					int price = rs.getInt(5);
					out.println("<h1>");
					out.println("Bookno: " + bookno);
					out.println("<br>");
					out.println("title: " + title);
					out.println("<br>");
					out.println("author: " + author);
					out.println("<br>");
					out.println("publication: " + publication);
					out.println("<br>");
					out.println("price: " + price);
					out.println("</h1>");
				}
				st.close();
				con.close();
				
				
			} catch(Exception e){
				e.printStackTrace();
			}
						
		}
	
	%>


</body>
</html>





