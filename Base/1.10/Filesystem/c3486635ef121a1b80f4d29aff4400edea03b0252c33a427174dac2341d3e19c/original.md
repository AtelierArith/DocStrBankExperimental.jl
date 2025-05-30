```
stat(file)
```

Return a structure whose fields contain information about the file. The fields of the structure are:

| Name    | Description                                                        |
|:------- |:------------------------------------------------------------------ |
| desc    | The path or OS file descriptor                                     |
| size    | The size (in bytes) of the file                                    |
| device  | ID of the device that contains the file                            |
| inode   | The inode number of the file                                       |
| mode    | The protection mode of the file                                    |
| nlink   | The number of hard links to the file                               |
| uid     | The user id of the owner of the file                               |
| gid     | The group id of the file owner                                     |
| rdev    | If this file refers to a device, the ID of the device it refers to |
| blksize | The file-system preferred block size for the file                  |
| blocks  | The number of such blocks allocated                                |
| mtime   | Unix timestamp of when the file was last modified                  |
| ctime   | Unix timestamp of when the file's metadata was changed             |
