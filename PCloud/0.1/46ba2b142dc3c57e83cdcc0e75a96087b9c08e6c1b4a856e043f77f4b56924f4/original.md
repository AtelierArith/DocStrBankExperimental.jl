```
savepubthumb(client::PCloudClient; kwargs...)
```

Create a thumbnail of a public link file and save it in the current user's filesystem

Same as savethumb, but works on public file identified by `code` (and `fileid` if link is to a folder)

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/savepubthumb.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'
  * `fileid::Int`: id of the file for thumb, if the link is to folder
  * `size::String`: WIDTHxHEIGHT
  * `topath::String`: filepath where to save the thumb
  * `tofolderid::Int`: folder id of the folder where to save the thumb
  * `toname::String`: filename to save the thumb

Use `fileid` or `path`

Use `topath` or `tofolderid`+`toname`

# Optional Arguments

  * `crop::Int`: If set, then the thumb will be cropped
  * `type::String`: If set to png, then the thumb will be in png format
  * `noover::Int`: If set, then will rise error on overwriting
