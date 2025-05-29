```
getthumbslinks(client::PCloudClient; kwargs...)
```

Get a link to thumbnails of a list of files

Takes in `fileids` parameter coma-separated list of fileids and returns thumbs for all the files.

`size`, `type` and `crop` work like in getthumblink and are all the same for all files.

If you need to generate multiple thumbnails `getthumbslinks` is preferable than multiple calls to `getthumblink` (even if pipelined)

`getthumbslinks` connects to multiple storage serves simultaneously to generate thumbs and in most cases it is just slightly slower than a single call to `getthumblink` even if multiple thumbnails are requested.

Source: https://docs.pcloud.com/methods/thumbnails/getthumbslinks.html

# Arguments

  * `fileids::String`: coma-separated list of fileids
  * `size::String`: WIDTHxHEIGHT

# Optional Arguments

  * `crop::Int`: If set, then the thumb will be cropped
  * `type::String`: If set to png, then the thumb will be in png format

# Output

The method returns an array `thumbs` with objects. Each object has `result` and `fileid` set.

If result is non-zero, `error` is also provided.

Otherwise `path`, `hosts`, `expires` and `size` are provided as in getfilelink.

# Output Example

```
{
    "result": 0,
    "thumbs": [
        {
            "expires": "Thu, 03 Oct 2013 23:04:48 +0000",
            "size": "32x32",
            "result": 0,
            "path": "/dFZVBFVZIpqkZIJZZdzeqC7Z3VZZmb0ZedrcUj5eXifiCM1JvlWCtfOG0zsy/th-FileID-32x32.png",
            "fileid": FileID,
            "hosts": [
                "c14.pcloud.com"
            ]
        },
        ...
    ]
}
```
