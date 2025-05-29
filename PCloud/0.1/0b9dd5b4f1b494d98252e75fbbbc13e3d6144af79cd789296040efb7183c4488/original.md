```
checksumfile(client::PCloudClient; kwargs...)
```

Calculate checksums of a given file

Source: https://docs.pcloud.com/methods/file/checksumfile.html

# Arguments

  * `fileid::Int`: id of the checked file
  * `path::String`: path to the checked file

Note that fileid or path could be used at once

# Output

Upon success returns `metadata`, `md5` and `sha1` checksums of the file.

# Output Example

```
{
    sha1: "ef2109a0b10ed2033f7ca11c0b62284c5e7fc860",
    md5: "4d200fbf4f7b5ea6eb1877d50e3d6c12",
    metadata: {
        size: 73269,
        parentfolderid: 0,
        width: 900,
        fileid: 1729212,
        contenttype: "image/jpeg",
        hash: 10681749967730528000,
        id: "f1729212",
        isfolder: false,
        thumb: true,
        name: "Simple image.jpg",
        modified: "Wed, 02 Oct 2013 15:05:09 +0000",
        isshared: false,
        height: 600,
        category: 1,
        ismine: true,
        created: "Wed, 02 Oct 2013 14:29:11 +0000",
        icon: "image"
    }
}
```
