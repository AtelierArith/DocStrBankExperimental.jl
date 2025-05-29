```
collection_rename(client::PCloudClient; kwargs...)
```

Renames a given collection owned by the current user.

Source: https://docs.pcloud.com/methods/collection/collection_rename.html

# Arguments

  * `collectionid::Int`: the id of the collection.
  * `name::String`: the new name of the collection.

# Output

On success returns the modified `collection`.

# Output Example

```
{
    "result": 0,
    "collection": [
        {
            "name": "my music",
            "id": 40,
            "ismine": true,
            "items": 8,
            "system": false,
            "type": "audio",
            "created": "Thu, 13 Feb 2014 12:34:22 +0000",
            "modified": "Mon, 17 Feb 2014 11:25:55 +0000",
            "contents": [ ]
        }
    ]
}
```
