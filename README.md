# Android Multiple File Selector Dialog



###Introduction

![ScreenShot](http://i.stack.imgur.com/LGvgr.png)

**Supports API 8(+)**

This is a free to use,change and reproduce Android Library file selector dialog whose birth arose from this question I posted on Stackoverflow

http://stackoverflow.com/questions/22095441/android-multiple-file-selector-chooser-dialog

This library starts a file/folder selector activity and returns the file(s) (Yes Multiple option too) or folder.
The library is still very simple and not very aesthetically pleasing so your contribution is highly welcome.

###Features
Thumbnails for Images

AutoScroll to last ScrollPosition on Back Pressed

New Folder Button

Button to access External/Internal Storage **not fully tested** :-)


###Usage
Add these activities in your manifest.
```
<activity
            android:name="paul.arian.fileselector.FileSelectionActivity" />
<activity
            android:name="paul.arian.fileselector.FolderSelectionActivity" />

```
Then also **add merge 1.04.jar** and **picasso jar** located in the repo to this library's build path or module

#### File Selector

To start the fileSelector 
first import.
```java
import paul.arian.fileselector.FileSelectionActivity;
```
use this code

```java
Intent intent = new Intent(getBaseContext(), FileSelectionActivity.class);
                startActivityForResult(intent, 0);
```

To capture the result, use this method.

```java
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if(requestCode == 0 && resultCode == RESULT_OK){
            ArrayList<File> Files = (ArrayList<File>) data.getSerializableExtra(FILES_TO_UPLOAD); //file array list
            String [] files_paths; //string array
            int i = 0;

            for(File file : Files){
                //String fileName = file.getName();
                String uri = file.getAbsolutePath();
                files_paths[i] = uri.toString(); //storing the selected file's paths to string array files_paths
                i++;
            }
        }else{
        }

    }

```

#### Folder Selector

To start folder selection activity,

import:
```java
import paul.arian.fileselector.FolderSelectionActivity;
```
to start use this code.
```java
Intent intent = new Intent(getBaseContext(), FolderSelectionActivity.class);
                startActivityForResult(intent, 2);
```
To capture, use this method.

```
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if(requestCode == 2 && resultCode == RESULT_OK){
            String FolderPath = data.getSerializableExtra(FILES_TO_UPLOAD).toString(); //The path of folder(directory) is stored in FolderPath string.
        }
    }
```

###### Credits
Massive credit goes to Arian JM of Madrid who created the majority of this library.

Here is his Github: https://github.com/ArianJM

Looking forward to your feedback, collaboration and assistence.

regards,

Paul Asiimwe,

Kampala, Uganda,

https://google.com/+PaulAsiimwe

https://twitter.com/_paulasiimwe
