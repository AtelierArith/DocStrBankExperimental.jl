```
gettreepublink(client::PCloudClient; kwargs...)
```

Creates and returns a public link to a virtual folder that is defined by requested tree.

Tree is identified by the following parameters:

  * `fileids`: comma-separated fileids
  * `folderids`: comma-separated folderids
  * `folderid:`: just one folderid - the contents of the folder will be dumped into the virtual folder instead of the folder itself

Also requires parameter `name` that will be the name of the virtual folder.

Same optional parameters as getfilepublink.

The created link will have similar properties to ones returned by getfolderpublink with one notable exception:

*Note:* Tree public links are snapshots of the requested files and folders at the time of creation and will not follow updates that will happen in the folders later.

Source: https://docs.pcloud.com/methods/public_links/gettreepublink.html

# Arguments

  * `folderid::Int`: folder id of the folder for public link
  * `path::String`: path to the folder for public link

Use `path` or `folderid`

# Optional Arguments

  * `expire::datetime`: Datetime when the link will stop working
  * `maxdownloads::Int`: Maximum number of downloads from this folder (even for the same file).
  * `maxtraffic::Int`: Maximum traffic that this link will consume (in bytes, started downloads will not be cut to fit in this limit)
  * `shortlink::Int`: If set, a short link will also be generated

# Output

On success returns

  * `linkid::Int`: ID that can be used to delete/modify this public link
  * `code::String`: link's code that can be used to retrieve the public link contents (with showpublink/getpublinkdownload)

If `shortlink` is set when calling, additonal- `linkid::Int`: ID that can be used to delete/modify this public link

  * `shortcode::String`: short code that can also be passed to showpublink/getpublinkdownload
  * `shortlink::String`: a full https link to pc.cd domain with shortcode appended

# Output Example

```
{
    "result": 0,
    "linkid": Link ID,
    "link": "https://my.pcloud.com/#page=publink&code=LinkCode",
    "code": "LinkCode"
}
```
