```
savethumb(client::PCloudClient; kwargs...)
```

Create a thumbnail of a file and save it in the current user's filesystem

takes the same parameters as getthumblink in addition to `topath` or `tofolderid`+`toname` and save the generated thumbnail as a file.

As usual by default this call overwrites existing files (saving the old one as revision) unless the `noover` parameter is set. In that case 'File or folder alredy exists.' error will be generated.

If `toname` is not provided, but `tofolderid` is, the file's original name is used for the thumbnail.

Similarly if `topath` ends with a slash ('/'), the original filename is appended.

Source: https://docs.pcloud.com/methods/thumbnails/savethumb.html

# Arguments

  * `fileid::Int`: id of the file for thumb
  * `path::String`: filepath to the file for thumb
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

# Output

On success returns `metadata`, `width` and `height`.

# Output Example

```
{
    result: 0,
    height: 32,
    width: 32,
    metadata: {
        path: "/my%20thumb.jpg",
        thumb: true,
        modified: "Thu, 03 Oct 2013 15:30:43 +0000",
        parentfolderid: 0,
        created: "Thu, 03 Oct 2013 15:30:43 +0000",
        ismine: true,
        category: 1,
        hash: 1154152318038973000,
        isshared: false,
        contenttype: "image/jpeg",
        fileid: 1818093,
        size: 650,
        id: "f1818093",
        icon: "image",
        name: "my thumb.jpg",
        isfolder: false
    }
}
```
