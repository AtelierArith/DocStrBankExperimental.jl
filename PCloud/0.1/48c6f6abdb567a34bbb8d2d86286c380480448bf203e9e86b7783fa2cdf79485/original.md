```
getvideolinks(client::PCloudClient; kwargs...)
```

Returns `variants` array of different quality/resolution versions of a video, identified by `fileid` (or `path`).

Each variant of the vide will have `path` and `hosts` (as with getfilelink), `width` and `height` of the video, `duration` of the video in seconds (floating point number sent as string), `fps` - frames per second rate of the video, `videobitrate` and `audiobitrate` will specify the bitrate of the video and audio, encoded by respectively `videocodec` and `audiocodec`. For the original video variant `isoriginal` will be true.

By default the content servers will send appropriate content-type for video files, this can be overridden with either `forcedownload` or `contenttype` optional parameters.

Optionally `skipfilename` works the same way as in getfilelink.

Source: https://docs.pcloud.com/methods/streaming/getvideolinks.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use `fileid` or `path`

# Optional Arguments

  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `maxspeed::Int`: limit the download speed
  * `skipfilename::Bool`: include the name of the file in the generated link

# Output

Explained above.

# Output Example

```
{
  "result": 0,
  "variants": [
    {
      "width": 640,
      "path": "/dFZwfHQZRRZ7Z7Z2b6cC7ZQ5ZZmb0ZK1TMI6SDeOy6pdx78UAVyfUhjd6y/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25",
      "isoriginal": false,
      "height": 400,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 501,
      "audiobitrate": 64,
      "audiocodec": "mp3",
      "duration": "245.4",
      "hosts": [
        "c58.pcloud.com",
        "c62.pcloud.com"
      ]
    },
    {
      "width": 1280,
      "path": "/dFZysHQZRRZ7Z7Z2b6cC7ZQ5ZZmb0Z8VoWFa3rb18W6dVJgc1O7hQdWCqV/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25",
      "isoriginal": false,
      "height": 720,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 1505,
      "audiobitrate": 128,
      "audiocodec": "mp3",
      "duration": "245.4",
      "hosts": [
        "c3.pcloud.com",
        "c17.pcloud.com"
      ]
    },
    {
      "rotate": 0,
      "path": "/dFZPzZRRZ7Z7Z2b6cC7ZQ5ZZmb0ZoogoFjJUdb01AMSvA1aYdHQmF9Ck/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25.00",
      "isoriginal": true,
      "audiosamplerate": 48000,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 5737,
      "audiocodec": "aac",
      "audiobitrate": 189,
      "width": 1280,
      "duration": "245.33",
      "height": 720,
      "hosts": [
        "c3.pcloud.com",
        "c65.pcloud.com"
      ]
    }
  ]
}
```
