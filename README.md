# How to install Umbraco in a LocalDB file

This tutorial will cover the installation of Umbraco 7.4 using SQL Server 2014 Express LocalDB as the database and Visual Studio Community 2015. It will assume that you already have Visual Studio and SQL Server installed. If you don't, these links may help:
* [Visual Studio Community 2015](https://www.visualstudio.com/products/visual-studio-community-vs)
* [SQL Server 2014 Express](https://msdn.microsoft.com/en-us/sqlserver2014express.aspx)

In Visual Studio create a new ASP.NET project, don't name it "Umbraco" or it will conflict with Umbraco own files. I'd also advise you to include folders and core references to MVC, but it's up to you.*(File -> New -> Project -> Templates -> Visual C# -> Web -> ASP.NET Web Application)*

In order to include Umbraco to your project run `Install-Package UmbracoCms` in the Package Manager Console. *(Tools -> NuGet Package Manager -> Package Manager Console)*

Create your LocalDB file by opening the SQL Server Object Explorer *(View -> SQL Server Object Explorer)*. Right-click on **"SQL Server"**, then **"Add SQL Server..."**, fill the server name for your SQL Server instance, it will likely to be **"(LocalDb)/v12.0"** - without the quotes. If you are not able to connect, maybe you don't have LocalDB running or you have to start it, in both cases you can follow the instructions here: [SqlLocalDB Utility](https://msdn.microsoft.com/en-us/library/hh212961.aspx)

When connected, expand your database — (LocalDb)/v12.0 — then right click on **"Databases"** and **"Add New Database"**. Here you will fill the name of your database (I'll name mine *UmbracoApplicationDb*) and the location of your project's *App_Data* folder, where your database file will be stored.

Run your project *(Debug -> Start Debugging* or *F5)*. You'll be prompted to modify your *Web.config* file to enable debugging, hit **OK**.

It will open your browser to Umbraco's installation. Fill your name, email, password and hit **"Customize"**. On **"Database type"** choose **"Microsoft SQL Server"**, then enter your server's name (*(LocalDb)/v12.0*) and the database's name (*UmbracoApplicationDb*), check **"Use integrated authentication"** and you're done!

:pig:
