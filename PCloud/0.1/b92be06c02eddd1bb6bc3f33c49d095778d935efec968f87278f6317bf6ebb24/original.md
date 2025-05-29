```
showpublink(client::PCloudClient; kwargs...)
```

Expects as parameter `code` that can be either 'code' or 'shortcode'.

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/showpublink.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Output

Returns `metadata` of the object the link points to.

If the object is folder, the `contents` field will be present (as in listfolder) with the (recursive) contents of the folder.

The field `isshared` of the returned `metadata` is always `false`, regardless of the real share status of the file/folder.

# Output Example

```
{
    result: 0,
    metadata: {
        isshared: false,
        icon: "folder",
        modified: "Wed, 18 Sep 2013 10:25:57 +0000",
        name: "Simple folder",
        id: "d21721",
        folderid: 21721,
        ismine: true,
        isfolder: true,
        created: "Wed, 18 Sep 2013 10:18:14 +0000",
        thumb: false,
        contents: [
            {
                icon: "audio",
                fileid: 618279,
                parentfolderid: 21721,
                size: 17675824,
                category: 3,
                isfolder: false,
                thumb: true,
                isshared: false,
                ismine: true,
                modified: "Wed, 18 Sep 2013 10:19:05 +0000",
                name: "Simple Audio.mp3",
                artist: "Pcloud",
                trackno: 1,
                genre: "Genre",
                contenttype: "audio/mpeg",
                title: "Simple Audio",
                album: "The album",
                id: "f618279",
                created: "Wed, 18 Sep 2013 10:18:15 +0000",
                hash: 6343095883282229000
            },
            ...
        ]
    }
}
```
