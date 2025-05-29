```
getpubtextfile(client::PCloudClient; kwargs...)
```

Download a file in different character encoding The file is streamed as response to this method by the content server.

Same as gettextfile, but works on public file identified by `code` (and `fileid` if link is to a folder)

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/getpubtextfile.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `fileid::Int`: id of the file, if the public link is to a folder
  * `fromencoding::String`: the original character encoding of the file (default: guess)
  * `toencoding::String`: requested character encoding of the output (default: utf-8)
  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
