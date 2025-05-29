```
getfilepublink(client::PCloudClient; kwargs...)
```

Creates and return a public link to a file.

The file is identified by `fileid` or `path`.

Source: https://docs.pcloud.com/methods/public_links/getfilepublink.html

# Arguments

  * `fileid::Int`: file id of the file for public link
  * `path::String`: path to the file for public link

Use `path` or `fileid`

# Optional Arguments

  * `expire::datetime`: Datetime when the link will stop working
  * `maxdownloads::Int`: Maximum number of downloads for this file
  * `maxtraffic::Int`: Maximum traffic that this link will consume (in bytes, started downloads will not be cut to fit in this limit)
  * `shortlink::Int`: If set, a short link will also be generated

# Output

On success returns

  * `linkid::Int`: ID that can be used to delete/modify this public link
  * `code::String`: link's code that can be used to retrieve the public link contents (with showpublink/getpublinkdownload)

If `shortlink` is set when calling, additonal

  * `linkid::Int`: ID that can be used to delete/modify this public link
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
