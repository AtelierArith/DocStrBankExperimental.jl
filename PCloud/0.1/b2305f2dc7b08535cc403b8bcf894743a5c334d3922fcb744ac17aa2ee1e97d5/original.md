```
gethlslink(client::PCloudClient; kwargs...)
```

Get a m3u8 playlist for live streaming for video file

Takes `fileid` (or `path`) of a video file and provides links (in the same way getfilelink does with `hosts` and `path`) from which a m3u8 playlist for HTTP Live Streaming can be downloaded.

Optional parameters are `abitrate`, `vbitrate`, `resolution` and `skipfilename`.

These have the same meaning as in getvideolink.

The defaults are the same as for getvideolink.

Source: https://docs.pcloud.com/methods/streaming/gethlslink.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use fileid or path

# Optional Arguments

  * `abitrate::Int`: audio bit rate in kilobits, from 16 to 320
  * `vbitrate::Int`: video bitrate in kilobits, from 16 to 4000
  * `resolution::String`: in pixels, from 64x64 to 1280x960, WIDTHxHEIGHT
  * `skipfilename::Int`: include the name of the file in the generated link

# Output

On success it will return array `hosts` with servers that have the file. The first server is the one we consider `best` for current download.

In `path` there will be a request you should send to server. You need to construct the URL yourself by concatenating http:// or https:// with one of the `hosts` (first one) and the `path`.

# Output Example

```
{
    expires: "Thu, 03 Oct 2013 01:27:42 +0000",
    result: 0,
    path: "/hash/My video.m3u8",
    hosts: [
        "c11.pcloud.com",
        "c20.pcloud.com"
    ]
}
```
