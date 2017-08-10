# Setting up NEO-CLI on Ubuntu 16.04

## 1. Install .NET core and dependencies
Link to the correct libraries and run an apt-get update. In this tutorial, dotnet-dev-1.0.4 is the latest version (line 4 of the code snippet below) but you can check https://www.microsoft.com/net/download/linux to see if there's an even more up-to-date version.

```
sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
sudo apt-get update
sudo apt-get install dotnet-dev-1.0.4
sudo apt-get install libleveldb-dev
reboot
```

## 2. Check to see if your installation is running properly
The commands below run a default installation of a simple "Hello World" app for .NET. If your .NET core installed correctly, you will see "Hello world" printed on your console after you run the line `dotnet run`.

```
dotnet new console -o hwapp
cd hwapp
dotnet restore
dotnet run 
```

## 3. Clone the NEO-CLI repository and install
The final step is to clone the github repo from the official NEO github. If you bump into an error that says the server cannot find the command git, then just run `apt-get install git` first. Ubuntu 16.04 should come with it stock, but not necessarily other versions of Ubuntu.

```
git clone https://github.com/neo-project/neo-cli.git
cd neo-cli
dotnet restore
dotnet msbuild neo-cli.sln
```

## 4. Run the Printed File Location to Start NEO CLI
Once the `dotnet msbuild neo-cli.sln` command completes, it will print out a file location that looks like `neo-cli -> CURRENT-FILE-LOCATION`. You can either create a symbolic link to that file with `ln -s CURRENT-FILE-LOCATION NEW-FILE-LOCATION`. Or you can just run it from the current file location. You can run it by doing either:

```
#If you didn't do the symbolic link
dotnet CURRENT-FILE-LOCATION

#If you did the symbolic link
dotnet NEW-FILE-LOCATION
```
