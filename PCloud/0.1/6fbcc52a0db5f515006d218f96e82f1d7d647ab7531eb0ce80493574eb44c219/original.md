```
listpublinks(client::PCloudClient; kwargs...)
```

Return a list of current user's public links

Takes no parameters

Source: https://docs.pcloud.com/methods/public_links/listpublinks.html

# Output

Returns all user's public links in array `publinks`. For each link the following fields are provided:

  * `linkid::Int`: this id can be used to delete or modify the link
  * `code::String`: see getfilepublink
  * `link::String`: see getfilepublink
  * `created::datetime`: date of the link creation
  * `modified::datetime`: date of last link modification
  * `metadata::contents`: metadata of the object the link points to (directories will not have )
  * `downloads::Int`: number of downloads
  * `traffic::Int`: traffic consumed so far by this link (bytes)

If the link has a short link:- `shortcode::String`: see getfilepublink

  * `shortlink::String`: see getfilepublink

If the link has a short link:- `expires::datetime`: date/time the link will expire (or has expired)

If the link has download limit:- `maxdownloads::Int`: maximum number of downloads for this link

If the link has traffic limit:- `maxtraffic::Int`: maximum traffic for this link

It is up to the implementations to detect and properly display links that have expired or reached the download or traffic limit.

# Output Example

```
{
    result: 0,
    publinks: [
        {
            downloads: 0,
            created: "Thu, 03 Oct 2013 13:06:04 +0000",
            link: "https://my.pcloud.com/#page=publink&code=fileCode",
            modified: "Thu, 03 Oct 2013 13:06:04 +0000",
            code: "fileCode",
            traffic: 2027520,
            linkid: linkid,
            metadata: {
                parentfolderid: 21721,
                created: "Wed, 18 Sep 2013 10:18:15 +0000",
                icon: "audio",
                size: 17675824,
                album: "Simple Album",
                artist: "pCloud",
                trackno: 1,
                isfolder: false,
                contenttype: "audio/mpeg",
                genre: "Audio",
                isshared: false,
                thumb: true,
                ismine: true,
                modified: "Wed, 18 Sep 2013 10:19:05 +0000",
                title: "Simple Audio",
                category: 3,
                hash: 6343095883282229000,
                name: "Simple Audio.mp3",
                fileid: 618279,
                id: "f618279"
            }
        },
        {
            downloads: 0,
            created: "Thu, 03 Oct 2013 13:11:44 +0000",
            link: "https://my.pcloud.com/#page=publink&code=folderCode",
            modified: "Thu, 03 Oct 2013 13:11:44 +0000",
            code: "folderCode",
            traffic: 0,
            linkid: linkid,
            metadata: {
                isfolder: true,
                folderid: 21721,
                isshared: true,
                thumb: false,
                modified: "Wed, 18 Sep 2013 10:25:57 +0000",
                parentfolderid: 0,
                created: "Wed, 18 Sep 2013 10:18:14 +0000",
                ismine: true,
                icon: "folder",
                name: "Simple Folder",
                id: "d21721"
            }
        }
    ]
}
```
