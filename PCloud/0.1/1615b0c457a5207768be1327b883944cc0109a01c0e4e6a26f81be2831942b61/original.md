```
savezipprogress(client::PCloudClient; kwargs...)
```

Get the progress in process of zipping file in the user's filesystem.

The process is started with the method savezip. On every zipped file the progress is updated. The process could be marked as ready, once when `files` equals `totalfiles` in the result.

Expects as parameter `progresshash` - key passed to savezip with the intention to observe the progress.

Please, use different `progresshash` for every call of savezip.

Source: https://docs.pcloud.com/methods/archiving/savezipprogress.html

# Optional Arguments

  * `progresshash::String`: the key to boserve the zipping process.

# Output

If there exists such zipping process, then the method returns:

  * `files::Int`: count of the already zipped files.
  * `totalfiles::Int`: total count of files to be zipped.
  * `bytes::Int`: size of the already zipped files.
  * `totalfiles::Int`: total size of the files to be zipped.

# Output Example

```
{
    "result": 0,
    "files": 34,
    "totalfiles": 129,
    "bytes": 263473,
    "totalbytes": 54750979
}
```
