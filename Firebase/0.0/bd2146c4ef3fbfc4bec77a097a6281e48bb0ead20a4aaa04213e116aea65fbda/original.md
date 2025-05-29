cloudstore_get(file2download = "")

Get a file cloud storage

# Example

```julia
init("[PROJECT_SDK].json")
cloudstore_init("https://firebasestorage.googleapis.com/v0/b/[PROJECT_ID].appspot.com/o")
cloudstore_get("/audio/data.mp3")
cloudstore_get("/data.mp3")
```
