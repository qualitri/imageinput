# ImageInput #
----------

Source: [http://daringfireball.net/projects/markdown/syntax#img](http://daringfireball.net/projects/markdown/syntax#img)

Transforms an html button input element into a input for easily uploading images.

**Easy for the end-user** : Image upload is done automatically with javascript/php while the user complete the form. 
The user can see its upload images and be warned of errors before submitting the form.

**Easy for the developper** : Set-up a beautiful form to upload images with only one line of code. 
After the form is submitted, the server code can just use the url set as a value of the input.
Thumbnails can be generated automatically.


**Features**

+ Customizable and automatic default images
+ Upload at click (Credits to http://code.google.com/p/upload-at-click/ )
+ Image size and format verification before submiting the form
+ Automatic thumbnails creation
+ No dependencies
+ Easy to use




##Usage ##

``` html
<input type="button" class="imageinput" name="myimgfield"
      data-name="input_image_1"
      data-height="800"
      data-width="1200"
      data-thumbnail-height="100"
      data-preview-height="150"
      data-path="path-on-your-webserver"
      data-filename="auto|fixed_name"
      data-sizerule="strict|proportion|free|crop|overflow|fit"
      data-formats="all|jpg,png,gif"
      data-text="message"
      data-class="className"
      data-default="src_your_image_default"
/>
```


###Parameters definition
All parameters stored in a input.


| Data Keys     | Type       | Description                      | Default   |
| ------------- |:----------:| -------------------------------- | :--------:|
| `data-name`   | string     | *set name of input image for submit form*  | |
| `data-height` | integer    | *desired image height in pixels* | 180px     |
| `data-width`  | integer    | *desired image width in pixels*  | 180px     |
| `data-thumbnail-height` | integer | `optional` *Thumbnail height in pixels If value is empty or the parameter does not exist, no thumbnail will be created. If activated, a new hidden input name "thumb-[name-of-your-imageinput]" will be added to your form with the thumnail path as a value* | " " |
| `data-preview-height` | integer    | `optional` *preview height in pixels, if you want to show a preview in your form with a different size than the original image (width will be calculated proportionnaly)* | `data-height` |
| `data-path`  | string   | `optional` *Desired subfolders in the public directory (see install) to upload your image*  | "www/public"   |
| `data-filename`  | string    | `optional` *Final name of the uploaded image, "auto" will generate an unique name* | "auto" |
| `data-sizerule`  | string    | `optional`<br> **strict** : *Forbid uploaded images with a different size than the parameters data-height and data-width*<br><br> **proportion** : *Allow only images with the same proportion than the parameters*<br><br> **fit** : *Allow anything* <br><br> **crop** : *Allow anything*<br><br> **overflow** : *Allow anything*  <br><br> **free** : *Allow anything* | "free" |
| `data-formats`  | string    | `optional` *desired image format extend upload*<br><br>**jpg,png,gif** :  *Allow only image of certain format separeted by commas*<br><br>**all** : <small>*Allow every format*</small>  | "all" |
| `data-text`  | string    | `optional` *if set, override the default text displayed in the bottom*  | "Upload Image" |
| `data-class`  | string    | `optional` *customize a class name for input image*  |  |
| `data-default`  | string    | `optional` *source the your image default fot image input*  |  |


## What it looks like ##

![alt tag](https://raw.github.com/qualitri/imageinput/master/screenshots/screenshot.png)


## Try it ##

http://qualitri.com/imageinput/demo.php


## Installation ##


Step 1/ Copy imageinput.php in a directory on your webserver, assure you that your webserver has the permissions to write new files and create new subdirectories in this direction.
``` 
Example (Apache default config): 
root@webserver$ cd /var/www/my-website/www
root@webserver$ mkdir public
root@webserver$ chown www-data:www-data public
root@webserver$ chmod 644 public
root@webserver$ cp /path/to/imageinput.php public/
```


Step 2/ Edit imageinput-min.js and change path to the IMAGE_DIR value and UPLOAD_MSG (optional): 
``` 
Example : 
var IMAGE_DIR = "/www/public";// absolute path to the directory created in step 1/ 
var UPLOAD_MSG = "Click to Upload";// text
```

Step 3/ Include imageinput-min.js and imageinput.css in every html page where you will need it.
``` 
Example : 
<link rel="stylesheet" href="//my-website/path/to/imageinput.css" />
<script src="//my-website/path/to/imageinput-min.js"></script>
```
