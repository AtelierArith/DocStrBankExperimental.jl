````
SFTPClient.walkdir(sftp::SFTP, root; topdown=true, follow_symlinks=false, onerror=throw)
Return an iterator that walks the directory tree of a directory.
The iterator returns a tuple containing `(rootpath, dirs, files)`.


# Examples
```julia
for (root, dirs, files) in walkdir(sftp, ".")
    println("Directories in $root")
    for dir in dirs
        println(joinpath(root, dir)) # path to directories
    end
    println("Files in $root")
    for file in files
        println(joinpath(root, file)) # path to files
    end
end
```
````
