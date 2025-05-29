```
getpublinkdownload(client::PCloudClient; kwargs...)
```

Returns link(s) where the file can be downloaded

Expects as parameter `code` that can be either 'code' or 'shortcode'.

The `code` could be obtained from:

getfilepublink - link to a single file

getfolderpublink - link to a folder

gettreepublink - link to a treegetcollectionpublink - link to a collectionIf the link is to a folder also expects `fileid`.

Optional parameters

*forcedownload*

*contenttype*

*skipfilename*

*maxspeed*work exaclty as explained in getfilelink.

This call is intentionally split from showpublink.

Getting download links for files you do not intend to download is considered

*bad behaviour*.

`getpublinkdownload` is to be called when user intents to actually download the file.

Source: https://docs.pcloud.com/methods/public_links/getpublinkdownload.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'
  * `fileid::Int`: File id, if the link is to a folder

# Optional Arguments

  * `forcedownload::Int`: Download with 'Content-Type' = 'application/octet-stream'
  * `contenttype::String`: Set 'Content-Type'
  * `maxspeed::Int`: limit the download speed
  * `skipfilename::Int`: include the name of the file in the generated link

# Output

Returns link(s) where the file can be downloaded (same as getfilelink`hosts`, `path` and `expire` are returned).

# Output Example

```
{
    result: 0,
    path: "/hash/My%20picture.jpg",
    expires: "Thu, 03 Oct 2013 01:06:49 +0000",
    hosts: [
        "c63.pcloud.com",
        "c1.pcloud.com"
    ]
}
```
