```
getthumb(client::PCloudClient; kwargs...)
```

Get a thumbnail of a file

Takes the same parameters as getthumblink, but returns the thumbnail over the current API connection.

Getting thumbnails from API servers is generally NOT faster than getting them from storage servers.

It makes sense only if you are reusing the (possibly expensive to open SSL) API connection.

Source: https://docs.pcloud.com/methods/thumbnails/getthumb.html

# Arguments

  * `fileid::Int`: id of the file for thumb
  * `path::String`: filepath to the file for thumb
  * `size::String`: WIDTHxHEIGHT

Use `fileid` or `path`

# Optional Arguments

  * `crop::Int`: If set, then the thumb will be cropped
  * `type::String`: If set to png, then the thumb will be in png format
