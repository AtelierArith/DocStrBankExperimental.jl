```
collection_create(client::PCloudClient; kwargs...)
```

Create a new collection for the current user.

Optionally, files could be given for the collection to fill it.

Source: https://docs.pcloud.com/methods/collection/collection_create.html

# Arguments

  * `name::Int`: the name of the new collection.

# Optional Arguments

  * `type::Int`: type of the collection.
  * `fileids::String`: comma-separated list of files to fill the collection.

Default type is 1 - playlist.

# Output

On success returns the new `collection` and the `metadata` of the items in the field `contents`, if such were given.

Also field `linkresult` will be added, if there were files to fill the collection. For its structure look at `collection_linkfiles`. If the linking was unsuccessful, then this field will be `false`.

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
