```
savezip(client::PCloudClient; kwargs...)
```

Create a zip file in the user's filesystem.

Recognizes the same parameters as getzip without `forcedownload` and `filename`.

Expects as parameter a defined tree.

Additionally expects the usual `topath` or `tofolderid`+`toname`.

Source: https://docs.pcloud.com/methods/archiving/savezip.html

# Optional Arguments

  * `timeoffset::String`: desired time offset
  * `topath::String`: path where to save the zip archive
  * `tofolderid::Int`: foldre id of the folder, where to save the zip archive
  * `toname::String`: filename of the desired zip archive
  * `progresshash::String`: key to retrieve the progress for the zipping process If you want to see the progres, please pass progresshash, different for every method call. To get the progress use savezipprogress

Use `topath` or `tofolderid` and `toname`

# Output

If successful creates the zip archive and returns its `metadata`.

# Output Example

```
{
    result: 0,
    metadata: {
        parentfolderid: 0,
        category: 5,
        hash: 3415575675870461400,
        ismine: true,
        created: "Thu, 03 Oct 2013 09:47:16 +0000",
        modified: "Thu, 03 Oct 2013 09:47:16 +0000",
        contenttype: "application/zip",
        path: "/Simple archive.zip",
        name: "Simple archive.zip",
        size: 17675984,
        isfolder: false,
        isshared: false,
        fileid: 1792497,
        icon: "archive",
        thumb: false,
        id: "f1792497"
    }
}
```
