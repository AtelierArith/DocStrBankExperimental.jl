```
getpubvideolinks(client::PCloudClient; kwargs...)
```

Returns `variants` array of different quality/resolution versions of a video in a public link.

Same as getvideolinks, but works on public file identified by `code` (and `fileid` if link is to a folder).

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/getpubvideolinks.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `fileid::Int`: id of the file, if the public link is to a folder
  * `forcedownload::Int`: Download with Content-Type = application/octet-stream
  * `contenttype::String`: Set Content-Type
  * `maxspeed::Int`: limit the download speed
  * `skipfilename::Bool`: include the name of the file in the generated link
