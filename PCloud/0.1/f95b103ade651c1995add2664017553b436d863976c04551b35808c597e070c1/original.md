```
getpubaudiolink(client::PCloudClient; kwargs...)
```

Create a link to a audio file of a public link file. The link could be used for streaming.

Same as getaudiolink, but works on public file identified by `code` (and `fileid` if link is to a folder)

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/getpubaudiolink.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `fileid::Int`: id of the file, if the public link is to a folder
  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `abitrate::Int`: audio bit rate in kilobits, from 16 to 320
