cloudstore_sendfile(file2download = "")

Send a file to cloud storage to store

# Example

```julia
init("[PROJECT_SDK].json")
cloudstore_init("https://firebasestorage.googleapis.com/v0/b/[PROJECT_ID].appspot.com/o")
cloudstore_sendfile("/audio/data.mp3")
```
