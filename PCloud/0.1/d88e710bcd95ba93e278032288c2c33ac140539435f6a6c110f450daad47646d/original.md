```
getzip(client::PCloudClient; kwargs...)
```

Receive a zip file from the user's filesystem.

Expects as parameter a defined tree.

Source: https://docs.pcloud.com/methods/archiving/getzip.html

# Optional Arguments

  * `forcedownload::Int`: If it is set, the content-type will be 'application/octet-stream', if not - 'application/zip'.
  * `filename::String`: If it is provided, this is sent back as 'Content-Disposition' header, forcing the browser to adopt this filename when downloading the file. Filename is passed unaltered, so it MUST include the .zip extension.
  * `timeoffset::String`: desired time offset

# Output

When successful it returns a zip archive over the current API connection with all the files and directories in the requested tree.

If the size of the resulting file is going to be over 4Gb or if it contains more than 65535 entries, the zip64 format is used, otherwise the file is plain zip. This is the fastest way to generate a zip file as the API server will construct the archive on-the-fly for you. Therefore the download will start instantly even with multi-gigabyte files.

Since zip files do not support timezone information for file modification times, by default all datetime values in the resulting zip file will be in UTC. Alternatively `timeoffset` parameter may be provided with the desired time offset in the usual +xxxx or -xxxx format. Also +/-xx:xx and some named timezones (EET, EEST, PST, CST and like) are supported.
