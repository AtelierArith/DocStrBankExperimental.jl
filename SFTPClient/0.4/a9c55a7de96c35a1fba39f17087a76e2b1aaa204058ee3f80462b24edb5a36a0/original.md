```
SFTPClient.download(
sftp::SFTP,
file_name::AbstractString,
 output = tempname();downloadDir::Union{String, Nothing}=nothing)

 Download a file. You can download it and use it directly, or save it to a file. 
 Specify downloadDir if you want to save downloaded files. You can also use broadcasting.
Example:

sftp = SFTP("sftp://test.rebex.net/pub/example/", "demo", "password")
files=readdir(sftp)
downloadDir="/tmp"
SFTPClient.download.(sftp, files, downloadDir=downloadDir)

You can also use it like this:
df=DataFrame(CSV.File(SFTPClient.download(sftp, "/mydir/test.csv")))
```
