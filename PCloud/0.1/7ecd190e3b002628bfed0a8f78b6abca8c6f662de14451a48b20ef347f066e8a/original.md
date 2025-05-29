```
getaudiolink(client::PCloudClient; kwargs...)
```

Get a streaming link for audio file Takes `fileid` (or `path`) of an audio (or video) file and provides links from which audio can be streamed in mp3 format. (Same way getfilelink does with `hosts` and `path`)

Optional parameters are `abitrate`, `forcedownload` and `contenttype`.

The default bitrate is 192kbit.

It can also be used to extract the audio track from a video.

The link itself supports the `start` GET parameter. This method can be used to play FLAC and other new formats on devices that only support mp3 playback.

Source: https://docs.pcloud.com/methods/streaming/getaudiolink.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use fileid or path

# Optional Arguments

  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `abitrate::Int`: audio bit rate in kilobits, from 16 to 320

# Output

On success it will return array `hosts` with servers that have the file. The first server is the one we consider `best` for current download.

In `path` there will be a request you should send to server. You need to construct the URL yourself by concatenating http:// or https:// with one of the `hosts` (first one) and the `path`.

# Output Example

```
{
    result: 0,
    expires: "Thu, 03 Oct 2013 01:23:12 +0000",
    path: "/hash/My Audio.mp3",
    hosts: [
        "c53.pcloud.com",
        "c58.pcloud.com"
    ]
}
```
