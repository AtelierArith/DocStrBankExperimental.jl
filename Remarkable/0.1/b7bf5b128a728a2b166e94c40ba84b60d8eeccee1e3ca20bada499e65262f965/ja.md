```
get_item(client, id::String, download = false)
get_item(client, id::RemarkableObject, download = false)
```

IDまたは既存の`RemarkableObject`を指定して`RemarkableObject`を返します。`download=true`を使用すると、ファイルをダウンロードするための`BlobURLGet`が得られます。
