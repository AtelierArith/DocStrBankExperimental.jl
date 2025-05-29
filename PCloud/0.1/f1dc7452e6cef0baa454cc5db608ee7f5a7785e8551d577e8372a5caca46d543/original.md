```
getvideolink(client::PCloudClient; kwargs...)
```

Get a streaming link for video file Takes `fileid` (or `path`) of a video file and provides links (same way getfilelink does with `hosts` and `path`) from which the video can be streamed with lower bitrate (and/or resolution).

The transcoded video will be in a FLV container with x264 video and mp3 audio, by default the video bitrate will be adapted to the connection speed in real time.

By default the content servers will send appropriate content-type for FLV files, this can be overridden with either `forcedownload` or `contenttype` optional parameters.

Optionally `skipfilename` works the same way as in getfilelink.

Transcoding specific optional parameters are:

  * `abitrate::Int`: audio bit rate in kilobits, from 16 to 320
  * `vbitrate::Int`: video bitrate in kilobits, from 16 to 4000
  * `resolution::String`: in pixels, from 64x64 to 1280x960, WIDTHxHEIGHT
  * `fixedbitrate::Bool`: if set, turns off adaptive streaming and the stream will be with a constant bitrate.

The video bitrate is only the initial if adaptive straming is used.

The default parameters (that should generally be OK for most cases) are:no change to video resolution (if you know your device resolution it might be a good idea to set `resolution`)initial video bitrate of 1000kbit/sec with adapting to connection speed128kbit audio bitrate Generated links, not the method itself accept the HTTP GET parameter `start`, that if present will skip that much seconds of the video.

Source: https://docs.pcloud.com/methods/streaming/getvideolink.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use fileid or path

# Optional Arguments

  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `maxspeed::Int`: limit the download speed
  * `skipfilename::Int`: include the name of the file in the generated link
  * `abitrate::Int`: audio bit rate in kilobits, from 16 to 320
  * `vbitrate::Int`: video bitrate in kilobits, from 16 to 4000
  * `resolution::String`: in pixels, from 64x64 to 1280x960, WIDTHxHEIGHT
  * `fixedbitrate::Bool`: if set, turns off adaptive streaming and the stream will be with a constant bitrate.

# Output

On success it will return array `hosts` with servers that have the file. The first server is the one we consider `best` for current download.

In `path` there will be a request you should send to server. You need to construct the URL yourself by concatenating http:// or https:// with one of the `hosts` (first one) and the `path`.

# Output Example

```
{
    "result": 0,
    "expires": "Thu, 03 Oct 2013 01:17:11 +0000",
    "path": "/hash/My video.mp4",
    "hosts": [
        "c11.pcloud.com",
        "c20.pcloud.com"
    ]
}
```
