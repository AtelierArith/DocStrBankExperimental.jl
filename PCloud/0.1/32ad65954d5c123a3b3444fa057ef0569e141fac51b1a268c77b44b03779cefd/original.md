```
getziplink(client::PCloudClient; kwargs...)
```

Receive a zip file link for files in the user's filesystem.

Recognizes the same parameters as getzip.

Expects as parameter a defined tree.

Unlike getzip, returns a download link(s) the same way getfilelink does - returns path, hosts and expire.

*Note : * This call is less efficient than getzip as the zip archive is created on our servers and only then you get a download link. So as fast as our servers are, it may take time to create a large archive.

The parameter `maxspeed` may be used if you wish to limit the download speed (in bytes per second) for this link.

Source: https://docs.pcloud.com/methods/archiving/getziplink.html

# Optional Arguments

  * `maxspeed::Int`: limit the download speed (in bytes per second) for this link.
  * `forcedownload::Int`: If it is set, the content-type will be 'application/octet-stream', if not - 'application/zip'.
  * `filename::String`: If it is provided, this is sent back as 'Content-Disposition' header, forcing the browser to adopt this filename when downloading the file. Filename is passed unaltered, so it MUST include the .zip extension.
  * `timeoffset::String`: desired time offset

# Output

On success it will return array `hosts` with servers that have the file.

The first server is the one we consider `best` for current download.

In `path` there will be a request you should send to server.

You need to construct the URL yourself by concatenating http:// or https:// with one of the `hosts` (first one) and the `path`.

# Output Example

```
{
    result: 0,
    path: "/dFZ73Y0ZtdPJZ3lZZhipqC7ZNVZZmb0ZHQp8Ed85S8HL874JvyYgMY8C1tbk/My%20picture.jpg",
    expires: "Thu, 03 Oct 2013 01:06:49 +0000",
    hosts: [
        "c63.pcloud.com",
        "c1.pcloud.com"
    ]
}
```
