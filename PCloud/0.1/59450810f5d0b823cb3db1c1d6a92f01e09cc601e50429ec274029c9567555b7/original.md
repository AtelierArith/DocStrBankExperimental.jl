```
listplshort(client::PCloudClient; kwargs...)
```

Return a list of current user's public links listpublinks

There is no `metadata` for each link, instead each link has `isfolder` field and `fileid` or `folderid` field.

Takes no parameters

Source: https://docs.pcloud.com/methods/public_links/listplshort.html

# Output

Returns all user's public links in array `publinks`. For each link the following fields are provided:

  * `linkid::Int`: this id can be used to delete or modify the link
  * `code::String`: see getfilepublink
  * `link::String`: see getfilepublink
  * `created::datetime`: date of the link creation
  * `modified::datetime`: date of last link modification
  * `isfolder::Bool`: true if the link is to folder
  * `folderid::Int`: the ID of the folder, if isfolder=true
  * `fileid::Int`: the ID of the file, if isfolder=false
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
            isfolder: false,
            traffic: 2027520,
            created: "Thu, 03 Oct 2013 13:06:04 +0000",
            fileid: 618279,
            linkid: 11660,
            downloads: 0,
            modified: "Thu, 03 Oct 2013 13:06:04 +0000",
            code: "fileCode",
            id: "f618279",
            link: "https://my.pcloud.com/#page=publink&code=fileCode"
        },
        {
            isfolder: true,
            traffic: 0,
            created: "Thu, 03 Oct 2013 13:11:44 +0000",
            id: "d21721",
            linkid: 11670,
            downloads: 0,
            folderid: 21721,
            code: "folderCode",
            modified: "Thu, 03 Oct 2013 13:11:44 +0000",
            link: "https://my.pcloud.com/#page=publink&code=folderCode"
        }
    ]
}
```
