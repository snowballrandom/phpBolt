# phpBolt - Best php encoder - ( ioncube alternative ) - 100% free 


First install **bolt.so** then you can encrypt php source code with **encryption.php** file. 

**[phpBolt.com](https://phpBolt.com)**

## How to install bolt.so ?
Download bolt.so file from https://phpbolt.com/ website. Then find extension directory. 
You can find extension directory by `phpinfo()` function. 
Then add `extension=bolt.so` in php.ini file and restart your server. 

How to Encrypt php source code ?

To encrypt a php file we will start with a simple example. This should be enough to get you started.

First make sure the bolt.so file is installed in your server enviroment. See above.

After you have the bolt.so successfully installed we will start by creating an virtual host to test our encryption.
Download this repo and extract it wherever you want. We will need the **encryption.php** file. 

This is the file that will do the encrypting for us. Copy this file to your virtual host that you just created.
After that we will create a file named **test.php** Open that file up and place the following inside:

```
<?php

echo 'Hello World!';

?>
```
Now copy this file and rename it to **test-orig.php**
Now oen up the **encryption.php** file and edit the **$src** and **$excludes** variables to look like this:

```
$src      = __DIR__;
$php_blot_key = "kyc7fh";
$excludes = array('encryption.php', 'test-orig.php');
```
Make sure that the directory where your virtual host is pointed at is writeable 777
Now point your browser to the your virtualhost and the file **encryption.php** 

**i.e. http://localhost/encryption.php**

You should get an output similar to the following:
```
Successfully Encrypted... Please check in /THE/DIRECTORY/OF/YOUR/VIRTUAL/HOST

```
Open up the test.php file in a text editor and you should see the following:
```
<?php bolt_decrypt( __FILE__ , PHP_BOLT_KEY); return 0;
    ##!!!##i4psiIu8tLxsVlaxr7S7bHOUsbi4u2yju764sG1zh1Y=
```
You will now need to edit this file by including the **PHP_BOLT_KEY** that you set in the **encryption.php** file. Your file should now look like this:
```
<?php 
define('PHP_BOLT_KEY', 'kyc7fh');
bolt_decrypt( __FILE__ , PHP_BOLT_KEY); return 0;
    ##!!!##i4psiIu8tLxsVlaxr7S7bHOUsbi4u2yju764sG1zh1Y=
```
Point your browser to the **test.php** file and you should see the words **"Hello World!"**

