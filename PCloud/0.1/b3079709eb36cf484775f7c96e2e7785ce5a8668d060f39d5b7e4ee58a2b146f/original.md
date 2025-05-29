```
getpubthumb(client::PCloudClient; kwargs...)
```

Get a thumbnail of a public file

Same as getthumb, but works on public file identified by `code` (and `fileid` if link is to a folder)

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/getpubthumb.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'
  * `fileid::Int`: id of the file for thumb, if the link is to folder
  * `size::String`: WIDTHxHEIGHT

# Optional Arguments

  * `crop::Int`: If set, then the thumb will be cropped
  * `type::String`: If set to png, then the thumb will be in png format
