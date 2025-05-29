cloudstore_sendfile(file2download = "")

ファイルをクラウドストレージに送信して保存します

# 例

```julia
init("[PROJECT_SDK].json")
cloudstore_init("https://firebasestorage.googleapis.com/v0/b/[PROJECT_ID].appspot.com/o")
cloudstore_sendfile("/audio/data.mp3")
```
