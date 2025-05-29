```
uploadfile(client::PCloudClient; kwargs...)
```

Upload a file.

String `path` or int `folderid` specify the target directory. If both are omitted the root folder is selected.

Parameter string `progresshash` can be passed. Same should be passed to uploadprogress method.

If `nopartial` is set, partially uploaded files will not be saved (that is when the connection breaks before file is read in full). If `renameifexists` is set, on name conflict, files will not be overwritten but renamed to name like `filename (2).ext`.

Multiple files can be uploaded, using POST with `multipart/form-data` encoding. If passed by POST, the parameters must come before files. All files are accepted, the name of the form field is ignored. Multiple files can come one or more HTML file controls.

Filenames must be passed as `filename` property of each file, that is - the way browsers send the file names.

If a file with the same name already exists in the directory, it is overwritten and old one is saved as revision. Overwriting a file with the same data does nothing except updating the `modification time` of the file.

Source: https://docs.pcloud.com/methods/file/uploadfile.html

# Arguments

  * `path::String`: path to the folder(discouraged)
  * `folderid::Int`: id of the folder
  * `filename::String`: the filename of each uploaded file

# Optional Arguments

  * `nopartial::Int`: If is set, partially uploaded files will not be saved
  * `progresshash::String`: hash used for observing upload progress
  * `renameifexists::Int`: if set, the uploaded file will be renamed, if file with the requested name exists in the folder.
  * `mtime::Int`: if set, file modified time is set. Have to be unix time seconds.
  * `ctime::Int`: if set, file created time is set. It's required to provide mtime to set ctime. Have to be unix time seconds.

# Output

Returns two arrays - fileids and `metadata`.

# Output Example

```
{
    "result": 0,
    "fileids": [
        1729212
    ],
    "metadata": [
        {
          "ismine": true,
          "id": "f1729212",
          "created": "Wed, 02 Oct 2013 14:29:11 +0000",
          "modified": "Wed, 02 Oct 2013 14:29:11 +0000",
          "hash": 10681749967730527559,
          "isshared": false,
          "isfolder": false,
          "category": 1,
          "parentfolderid": 0,
          "icon": "image",
          "fileid": 1729212,
          "height": 600,
          "width": 900,
          "path": "/Simple image.jpg",
          "name": "Simple image.jpg",
          "contenttype": "image/jpeg",
          "size": 73269,
          "thumb": true
        }
    ]
}

```
