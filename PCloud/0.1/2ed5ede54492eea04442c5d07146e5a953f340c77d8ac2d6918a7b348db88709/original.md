```
gettextfile(client::PCloudClient; kwargs...)
```

Download a file in different character encoding Takes `fileid` (or `path`) as parameter and returns contents of the file in different character encoding. The file is streamed as response to this method by the content server.

Optional parameter `fromencoding` specify the original character encoding of the file. If ommited it will be guessed based on the contents of the file.

Optional parameter `toencoding` specify the requested character encoding for the output. The default is `utf-8`.

If the optional parameter `forcedownload` is set, the file will be served by the server with content type application/octet-stream, which typically forces user agents to save the file.

Alternatively you can provide parameter `contenttype` with the Content-Type you wish the server to send. If these parameters are not set, the content type will depend on the extension of the file.

Source: https://docs.pcloud.com/methods/streaming/gettextfile.html

# Arguments

  * `fileid::Int`: ID of the renamed file
  * `path::String`: Path to the renamed file

Use fileid or path

# Optional Arguments

  * `fromencoding::String`: the original character encoding of the file (default: guess)
  * `toencoding::String`: requested character encoding of the output (default: utf-8)
  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type

# Output

On success this method outputs the data by the API server. No links to content servers are provided. Unless you provide invalid encodings in `fromecoding` or `toencoding` you can safely assume that this method will not fail.
