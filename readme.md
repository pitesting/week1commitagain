R version 3.4.0 (2017-04-21) -- "You Stupid Darkness"
Copyright (C) 2017 The R Foundation for Statistical Computing
Platform: x86_64-w64-mingw32/x64 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

> if(!file.exists("exdata-data-household_power_consumption.zip")) {
  +     temp <- tempfile()
  +     download.file("http://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip",temp)
  +     file <- unzip(temp)
  +     unlink(temp)
  + }
trying URL 'http://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip'
Content type 'application/zip' length 20640916 bytes (19.7 MB) 
downloaded 19.7 MB

> power <- read.table(file, header=T, sep=";")
> power$Date <- as.Date(power$Date, format="%d/%m/%Y")
> df <- power[(power$Date=="2007-02-01") | (power$Date=="2007-02-02"),]
> df$Global_active_power <- as.numeric(as.character(df$Global_active_power))
> df$Global_reactive_power <- as.numeric(as.character(df$Global_reactive_power))
> df$Voltage <- as.numeric(as.character(df$Voltage))
> df <- transform(df, timestamp=as.POSIXct(paste(Date, Time)), "%d/%m/%Y %H:%M:%S")
> df$Sub_metering_1 <- as.numeric(as.character(df$Sub_metering_1))
> df$Sub_metering_2 <- as.numeric(as.character(df$Sub_metering_2))
> df$Sub_metering_3 <- as.numeric(as.character(df$Sub_metering_3))
> plot1 <- function() {
  +     hist(df$Global_active_power, main = paste("Global Active Power"), col="red", xlab="Global Active Power (kilowatts)")
  +     dev.copy(png, file="plot1.png", width=480, height=480)
  +     dev.off()
  +     cat("Plot1.png has been saved in", getwd())
  + }
> plot1()
Plot1.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> plot1 <- function() {
  +     plot(df$timestamp,df$Global_active_power, type="l", xlab="", ylab="Global Active Power (kilowatts)")
  +     dev.copy(png, file="plot2.png", width=480, height=480)
  +     dev.off()
  +     cat("plot2.png has been saved in", getwd())
  + }
> plot1()
plot2.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> plot3 <- function() {
  +     plot(df$timestamp,df$Sub_metering_1, type="l", xlab="", ylab="Energy sub metering")
  +     lines(df$timestamp,df$Sub_metering_2,col="red")
  +     lines(df$timestamp,df$Sub_metering_3,col="blue")
  +     legend("topright", col=c("black","red","blue"), c("Sub_metering_1  ","Sub_metering_2  ", "Sub_metering_3  "),lty=c(1,1), lwd=c(1,1))
  +     dev.copy(png, file="plot3.png", width=480, height=480)
  +     dev.off()
  +     cat("plot3.png has been saved in", getwd())
  + }
> plot3()
plot3.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> plot4 <- function() {
  +     par(mfrow=c(2,2))
  +     
    +     ##PLOT 1
    +     plot(df$timestamp,df$Global_active_power, type="l", xlab="", ylab="Global Active Power")
  +     ##PLOT 2
    +     plot(df$timestamp,df$Voltage, type="l", xlab="datetime", ylab="Voltage")
  +     
    +     ##PLOT 3
    +     plot(df$timestamp,df$Sub_metering_1, type="l", xlab="", ylab="Energy sub metering")
  +     lines(df$timestamp,df$Sub_metering_2,col="red")
  +     lines(df$timestamp,df$Sub_metering_3,col="blue")
  +     legend("topright", col=c("black","red","blue"), c("Sub_metering_1  ","Sub_metering_2  ", "Sub_metering_3  "),lty=c(1,1), bty="n", cex=.5) #bty removes the box, cex shrinks the text, spacing added after labels so it renders correctly
  +     
    +     #PLOT 4
    +     plot(df$timestamp,df$Global_reactive_power, type="l", xlab="datetime", ylab="Global_reactive_power")
  +     
    +     #OUTPUT
    +     dev.copy(png, file="plot4.png", width=480, height=480)
  +     dev.off()
  +     cat("plot4.png has been saved in", getwd())
  + }
> plot4()
plot4.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> > plot1()
Error: unexpected '>' in ">"
> Plot1.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
Error: unexpected symbol in "Plot1.png has"
> > plot1 <- function() {
  Error: unexpected '>' in ">"
  >     +     plot(df$timestamp,df$Global_active_power, type="l", xlab="", ylab="Global Active Power (kilowatts)")
  Error in +plot(df$timestamp, df$Global_active_power, type = "l", xlab = "",  : 
                   invalid argument to unary operator
                 >     +     dev.copy(png, file="plot2.png", width=480, height=480)
                 png 
                 4 
                 >     +     dev.off()
                 RStudioGD 
                 2 
                 >     +     cat("plot2.png has been saved in", getwd())
                 plot2.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
                 Error in +cat("plot2.png has been saved in", getwd()) : 
                   invalid argument to unary operator
                 >     + }
Error: unexpected '}' in "    + }"
> > plot1()
Error: unexpected '>' in ">"
> 
  > > if(!file.exists("exdata-data-household_power_consumption.zip")) {
    Error: unexpected '>' in ">"
    >     +     temp <- tempfile()
    Error in +temp <- tempfile() : could not find function "+<-"
    >     +     download.file("http://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip",temp)
    trying URL 'http://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip'
    Content type 'application/zip' length 20640916 bytes (19.7 MB)
    downloaded 19.7 MB
    
    [1] 0
    >     +     file <- unzip(temp)
    Error in +file <- unzip(temp) : could not find function "+<-"
    >     +     unlink(temp)
    [1] 0
    >     + }
Error: unexpected '}' in "    + }"
> trying URL 'http://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip'
Error: unexpected symbol in "trying URL"
> Content type 'application/zip' length 20640916 bytes (19.7 MB)
Error: unexpected symbol in "Content type"
> downloaded 19.7 MB
Error: unexpected numeric constant in "downloaded 19.7"
> 
  > > power <- read.table(file, header=T, sep=";")
Error: unexpected '>' in ">"
> > power$Date <- as.Date(power$Date, format="%d/%m/%Y")
Error: unexpected '>' in ">"
> > df <- power[(power$Date=="2007-02-01") | (power$Date=="2007-02-02"),]
Error: unexpected '>' in ">"
> > df$Global_active_power <- as.numeric(as.character(df$Global_active_power))
Error: unexpected '>' in ">"
> > df$Global_reactive_power <- as.numeric(as.character(df$Global_reactive_power))
Error: unexpected '>' in ">"
> > df$Voltage <- as.numeric(as.character(df$Voltage))
Error: unexpected '>' in ">"
> > df <- transform(df, timestamp=as.POSIXct(paste(Date, Time)), "%d/%m/%Y %H:%M:%S")
Error: unexpected '>' in ">"
> > df$Sub_metering_1 <- as.numeric(as.character(df$Sub_metering_1))
Error: unexpected '>' in ">"
> > df$Sub_metering_2 <- as.numeric(as.character(df$Sub_metering_2))
Error: unexpected '>' in ">"
> > df$Sub_metering_3 <- as.numeric(as.character(df$Sub_metering_3))
Error: unexpected '>' in ">"
> > plot1 <- function() {
  Error: unexpected '>' in ">"
  >     +     hist(df$Global_active_power, main = paste("Global Active Power"), col="red", xlab="Global Active Power (kilowatts)")
  Error in +hist(df$Global_active_power, main = paste("Global Active Power"),  : 
                   invalid argument to unary operator
                 >     +     dev.copy(png, file="plot1.png", width=480, height=480)
                 png 
                 4 
                 >     +     dev.off()
                 RStudioGD 
                 2 
                 >     +     cat("Plot1.png has been saved in", getwd())
                 Plot1.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
                 Error in +cat("Plot1.png has been saved in", getwd()) : 
                   invalid argument to unary operator
                 >     + }
Error: unexpected '}' in "    + }"
> > plot1()
Error: unexpected '>' in ">"
> plot4 <- function() {
  +     par(mfrow=c(2,2))
  +     
    +     ##PLOT 1
    +     plot(df$timestamp,df$Global_active_power, type="l", xlab="", ylab="Global Active Power")
  +     ##PLOT 2
    +     plot(df$timestamp,df$Voltage, type="l", xlab="datetime", ylab="Voltage")
  +     
    +     ##PLOT 3
    +     plot(df$timestamp,df$Sub_metering_1, type="l", xlab="", ylab="Energy sub metering")
  +     lines(df$timestamp,df$Sub_metering_2,col="red")
  +     lines(df$timestamp,df$Sub_metering_3,col="blue")
  +     legend("topright", col=c("black","red","blue"), c("Sub_metering_1  ","Sub_metering_2  ", "Sub_metering_3  "),lty=c(1,1), bty="n", cex=.5) #bty removes the box, cex shrinks the text, spacing added after labels so it renders correctly
  +     
    +     #PLOT 4
    +     plot(df$timestamp,df$Global_reactive_power, type="l", xlab="datetime", ylab="Global_reactive_power")
  +     
    +     #OUTPUT
    +     dev.copy(png, file="plot4.png", width=480, height=480)
  +     dev.off()
  +     cat("plot4.png has been saved in", getwd())
  + }
> plot4()
plot4.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> plot4 <- function() {
  +     par(mfrow=c(2,2))
  +     
    +     ##PLOT 1
    +     plot(df$timestamp,df$Global_active_power, type="l", xlab="", ylab="Global Active Power")
  +     ##PLOT 2
    +     plot(df$timestamp,df$Voltage, type="l", xlab="datetime", ylab="Voltage")
  +     
    +     ##PLOT 3
    +     plot(df$timestamp,df$Sub_metering_1, type="l", xlab="", ylab="Energy sub metering")
  +     lines(df$timestamp,df$Sub_metering_2,col="red")
  +     lines(df$timestamp,df$Sub_metering_3,col="blue")
  +     legend("topright", col=c("black","red","blue"), c("Sub_metering_1  ","Sub_metering_2  ", "Sub_metering_3  "),lty=c(1,1), bty="n", cex=.5) #bty removes the box, cex shrinks the text, spacing added after labels so it renders correctly
  +     
    +     #PLOT 4
    +     plot(df$timestamp,df$Global_reactive_power, type="l", xlab="datetime", ylab="Global_reactive_power")
  +     
    +     #OUTPUT
    +     dev.copy(png, file="plot4.png", width=480, height=480)
  +     dev.off()
  +     cat("plot4.png has been saved in", getwd())
  + }
> plot4()
plot4.png has been saved in D:/Coursera/Explanitory Data/w1expdatamaster
> 