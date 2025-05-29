```
savepubzip(client::PCloudClient; kwargs...)
```

Create a zip archive file of a public link file in the current user filesystem

Same as savezip, but works on public file identified by `code`

Takes `code` and optional parameters to define a tree and streams a zip file.

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/savepubzip.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `timeoffset::String`: desired time offset
  * `topath::String`: path where to save the zip archive
  * `tofolderid::Int`: foldre id of the folder, where to save the zip archive
  * `toname::String`: filename of the desired zip archive

# Output

If successful creates the zip archive and returns its `metadata`.
