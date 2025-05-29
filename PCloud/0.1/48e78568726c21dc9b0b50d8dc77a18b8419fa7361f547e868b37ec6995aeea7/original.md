```
collection_unlinkfiles(client::PCloudClient; kwargs...)
```

Remove files from a current collection.

There are three methods to remove files from the collection:

all items in the collectionsremove fileids from the collectionremove items at given positionsThe priority is the method checks is position, then all , then fileids.

Source: https://docs.pcloud.com/methods/collection/collection_unlinkfiles.html

# Arguments

  * `collectionid::Int`: the id of the collection.

# Optional Arguments

  * `all::Int`: if set, all files from the collection are unlinked
  * `positions::String`: comma-separated list of positions to be unlinked
  * `fileids::String`: comma-separated list of fileids to be unlinked

*Note:* Use one of this parameters.

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
            "modified": "Mon, 18 Feb 2014 14:25:55 +0000",
            "contents": [ ]
        }
    ]
}
```
