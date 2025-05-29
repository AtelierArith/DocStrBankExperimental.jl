```
get_item(client, id::String, download = false)
get_item(client, id::RemarkableObject, download = false)
```

Return a `RemarkableObject` given an ID or an existing `RemarkableObject`, using `download=true` will give the `BlobURLGet` to download the files
