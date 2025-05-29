```
collection_list(client::PCloudClient; kwargs...)
```

Get a list of the collections, that are owned from the current user.

Optionally, the items in the collections could be returned and the collections could be filtered by type.

The system collections of the current user are genereated on the first call of this method.

This method removes from the collection all items that could not be found at the time of invocation. Reasons are, for example, the files were moved to trash or there were in a shared folder, that now is not shared.

Source: https://docs.pcloud.com/methods/collection/collection_list.html

# Optional Arguments

  * `type::Int`: Filter type of the collection. 1 is for playlists.
  * `showfiles::Int`: If set, then contents of the collection will be filled with metadata of the files in the collection.
  * `pagesize::Int`: If set and showfiles is set, then the items in contents will be limited to this count.

# Output

On success returns the `collections` and optionally the `metadata` of the first items in the collection in the field `contents`.

# Output Example

```
{
    "result": 0,
    "collections": [
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
        } ,
        { 
            "name": "Most Listened",
            "id": 38,
            "ismine": true,
            "items": 0,
            "system": true,
            "type": "audio",
            "created": "Wed, 12 Feb 2014 11:51:00 +0000",
            "modified": "Wed, 12 Feb 2014 11:51:00 +0000",
            "contents": [ ]
        } ,

        ...

    ]
}
```
