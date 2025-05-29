```
getpubziplink(client::PCloudClient; kwargs...)
```

Create a link to a zip archive file of a public link file

Same as getziplink, but works on public file identified by `code`

`getpubziplink` is slower and less efficient than getpubzip and takes time to generate the zip file as opposed to the former which starts the download right away.

Takes `code` and optional parameters to define a tree and streams a zip file.

The `code` could be obtained from:getfilepublink - link to a single filegetfolderpublink - link to a foldergettreepublink - link to a treegetcollectionpublink - link to a collection

Source: https://docs.pcloud.com/methods/public_links/getpubziplink.html

# Arguments

  * `code::String`: either 'code' or 'shortcode'

# Optional Arguments

  * `forcedownload::Int`: If it is set, the content-type will be 'application/octet-stream', if not - 'application/zip'.
  * `filename::String`: If it is provided, this is sent back as 'Content-Disposition' header, forcing the browser to adopt this filename when downloading the file. Filename is passed unaltered, so it MUST include the .zip extension.
  * `timeoffset::String`: desired time offset
