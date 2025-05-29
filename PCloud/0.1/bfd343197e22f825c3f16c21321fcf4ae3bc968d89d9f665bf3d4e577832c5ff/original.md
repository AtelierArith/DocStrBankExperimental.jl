```
collection_linkfiles(client::PCloudClient; kwargs...)
```

Appends files to the collection.

The files will be added at the end of the collection. If you want to insert the files at another position, then link them via this method and then use `collection_move`.

This method preserves the relative order given in the fileids field.

Duplicates are not allowed to be met in the collections.

Source: https://docs.pcloud.com/methods/collection/collection_linkfiles.html

# Arguments

  * `collectionid::Int`: the id of the collection.
  * `fileids::String`: comma-separated list of ids of the files to be added.

# Optional Arguments

  * `noitems::Int`: if set, then linkresult will be empty

# Output

On success returns the updated `collection`.

`linkresult` contains the result for all items, unless `noitems` is set. It has the format:

  * `result::Int`: code of the operation. 0 means success, otherwise the file could not be linked.
  * `fileid::Int`: the id of the file that is linked
  * `message::String`: if an error occures, then this the message of the error. Not set, if successful.
  * `metadata::metadata`: the metadata of the linked file, if linked successfully. The fields are added:position - where the item is added to the collectionadded - when the item was linked to the collection

# Output Example

```
{
    "result": 0,
    "linkresult": [
    {
        "fileid": "599457",
        "result": 0,
        "metadata": {
            "id": "f599457",
            "fileid": 599457,
            "contenttype": "audio/mpeg",

            "position": 9,
            "added": "Tue, 18 Feb 2014 11:16:24 +0000",

            "created": "Mon, 16 Sep 2013 12:10:32 +0000",
            "modified": "Mon, 16 Sep 2013 12:10:32 +0000",
            "hash": 1682158607045670700,
            "icon": "audio",
            "parentfolderid": 21383,
            "ismine": true,
            "isshared": false,
            "isfolder": false,
            "name": "Demo Audio 2.mp3",
            "category": 3,
            "thumb": false,
            "size": 1442376
        }
    },
    {
        "fileid": "123",
        "result": 2009,
        "message": "File not found."
    },

    ...

    ],
    "collection": {
        "id": 40,
        "name": "my music",
        "type": "audio",
        "ismine": true,
        "system": false,
        "items": 11,
        "created": "Thu, 13 Feb 2014 12:34:22 +0000",
        "modified": "Tue, 18 Feb 2014 11:16:24 +0000",
        "contents": []
    }
}
```
