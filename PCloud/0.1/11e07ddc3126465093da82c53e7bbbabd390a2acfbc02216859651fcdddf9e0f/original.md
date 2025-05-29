```
getfilelink(client::PCloudClient; kwargs...)
```

Get a download link for file Takes `fileid` (or `path`) as parameter and provides links from which the file can be downloaded.

If the optional parameter `forcedownload` is set, the file will be served by the content server with content type application/octet-stream, which typically forces user agents to save the file.

Alternatively you can provide parameter `contenttype` with the Content-Type you wish the content server to send. If these parameters are not set, the content type will depend on the extension of the file.

Parameter `maxspeed` may be used if you wish to limit the download speed (in bytes per second) for this download.

Finally you can set `skipfilename` so the link generated will not include the name of the file.

Source: https://docs.pcloud.com/methods/streaming/getfilelink.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use fileid or path

# Optional Arguments

  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `maxspeed::Int`: limit the download speed
  * `skipfilename::Int`: include the name of the file in the generated link

# Output

On success it will return array `hosts` with servers that have the file. The first server is the one we consider `best` for current download.

In `path` there will be a request you should send to server.

You need to construct the URL yourself by concatenating http:// or https:// with one of the `hosts` (first one) and the `path`.

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
