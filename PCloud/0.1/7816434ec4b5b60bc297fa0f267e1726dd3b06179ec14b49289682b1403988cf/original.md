```
collection_details(client::PCloudClient; kwargs...)
```

Get details for a given collection and the items in it.

Optionally, paging could be used for the results in the collection.

This method removes from the collection all items that could not be found at the time of invocation. Reasons are, for example, the files were moved to trash or there were in a shared folder, that now is not shared. For that reason, when paging is used, the page could have less results than the pagesize and more pages to be available.

Source: https://docs.pcloud.com/methods/collection/collection_details.html

# Arguments

  * `collectionid::Int`: the id of the collection.

# Optional Arguments

  * `page::Int`: the number of the page, for which results are shown.
  * `pagesize::Int`: the size of the page.

Default page is 0, which is all items.

# Output

On success returns the `collection` and the `metadata` of the items in the field `contents`.

# Output Example

```
{
    "result": 0,
    "collection": {
        "id": 40,
        "type": "audio",
        "system": false,
        "ismine": true,
        "items": 11,
        "created": "Thu, 13 Feb 2014 12:34:22 +0000",
        "modified": "Tue, 18 Feb 2014 11:16:24 +0000",
        "name": "my music",
        "contents": [
            {
                "id": "f599457",
                "fileid": 599457,
                "name": "Demo Audio 2.mp3",
                "parentfolderid": 21383,

                "position": 1,
                "added": "Mon, 17 Feb 2014 15:53:48 +0000",

                "isshared": false,
                "category": 3,
                "ismine": true,
                "icon": "audio",
                "created": "Mon, 16 Sep 2013 12:10:32 +0000",
                "hash": 1682158607045670700,
                "isfolder": false,
                "contenttype": "audio/mpeg",
                "modified": "Mon, 16 Sep 2013 12:10:32 +0000",
                "size": 142376,
                "thumb": false
            },

            ...

        ]
    }
}
```
