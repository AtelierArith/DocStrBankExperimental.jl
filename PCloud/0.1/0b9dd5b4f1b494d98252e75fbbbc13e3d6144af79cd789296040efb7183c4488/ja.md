```
checksumfile(client::PCloudClient; kwargs...)
```

指定されたファイルのチェックサムを計算します

ソース: https://docs.pcloud.com/methods/file/checksumfile.html

# 引数

  * `fileid::Int`: チェックされるファイルのID
  * `path::String`: チェックされるファイルのパス

fileidまたはpathのいずれかを同時に使用できます

# 出力

成功した場合、ファイルの`metadata`、`md5`および`sha1`チェックサムを返します。

# 出力例

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
