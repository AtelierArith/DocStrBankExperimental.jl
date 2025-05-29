```
uploadprogress(client::PCloudClient; kwargs...)
```

Get upload progress of a file.

MUST be sent to the same api server that you are currently uploading to. The parameter string `progresshash` MUST be passed and must contain the same value that was passed in the upload request that is currently in progress.

Source: https://docs.pcloud.com/methods/file/uploadprogress.html

# Arguments

  * `progresshash::String`: hash defining the upload, same as sent to uploadfile

# Output

Upon success returns fields:

  * `total`: total bytes to be transferred (that is the Content-Length of the upload request)
  * `uploaded`: bytes uploaded so far
  * `currentfile`: the filename of the file that is currently being uploaded
  * `files`: metadata of the already uploaded files (without the current one)
  * `finished`: indicates if the upload is finished or not

For finished uploads `currentfile` and `currentfileuploaded` are not present.

Keep in mind that `total` and `uploaded` include the protocol overhead and metadata, `currentfileuploaded` does not.

# Output Example

```
{
    "currentfile": "Simple file",
    "currentfileuploaded": 4199743,
    "result": 0,
    "total": 7768889,
    "filenumber": 1,
    "uploaded": 4199936,
    "finished": false,
    "files": [ ]
}
```
