```
getpubzip(client::PCloudClient; kwargs...)
```

Create a zip archive file of a public link file and download it

Same as getzip, but works on public file identified by `code` (and `fileid` if link is to a folder)

Takes `code` and optional parameters to define a tree and streams a zip file.

The `code` could be obtained from:

getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection`filename`, `forcedownload` and `timeoffset` optional parameters work the same way as in getzip.

Source: https://docs.pcloud.com/methods/public_links/getpubzip.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `forcedownload::Int`: If it is set, the content-type will be 'application/octet-stream', if not - 'application/zip'.
  * `filename::String`: If it is provided, this is sent back as 'Content-Disposition' header, forcing the browser to adopt this filename when downloading the file. Filename is passed unaltered, so it MUST include the .zip extension.
  * `timeoffset::String`: desired time offset

# Output

When successful it returns a zip archive over the current API connection with all the files and directories in the requested tree.
