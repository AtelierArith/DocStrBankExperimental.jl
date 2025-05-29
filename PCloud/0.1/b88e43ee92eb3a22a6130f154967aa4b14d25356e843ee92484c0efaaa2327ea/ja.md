```
getthumbslinks(client::PCloudClient; kwargs...)
```

ファイルのリストのサムネイルへのリンクを取得します

`fileids` パラメータにはカンマ区切りのファイルIDのリストを受け取り、すべてのファイルのサムネイルを返します。

`size`、`type`、および `crop` は `getthumblink` と同様に機能し、すべてのファイルに対して同じです。

複数のサムネイルを生成する必要がある場合は、`getthumbslinks` の方が複数回の `getthumblink` 呼び出し（パイプライン化されていても）よりも好ましいです。

`getthumbslinks` は、サムネイルを生成するために複数のストレージサーバーに同時に接続し、ほとんどの場合、複数のサムネイルが要求されても、単一の `getthumblink` 呼び出しよりもわずかに遅くなります。

出典: https://docs.pcloud.com/methods/thumbnails/getthumbslinks.html

# 引数

  * `fileids::String`: カンマ区切りのファイルIDのリスト
  * `size::String`: WIDTHxHEIGHT

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: png に設定されている場合、サムネイルは png 形式になります

# 出力

このメソッドは、`result` と `fileid` が設定されたオブジェクトを含む配列 `thumbs` を返します。

結果がゼロでない場合、`error` も提供されます。

そうでない場合、`path`、`hosts`、`expires`、および `size` が `getfilelink` と同様に提供されます。

# 出力例

```
{
    "result": 0,
    "thumbs": [
        {
            "expires": "Thu, 03 Oct 2013 23:04:48 +0000",
            "size": "32x32",
            "result": 0,
            "path": "/dFZVBFVZIpqkZIJZZdzeqC7Z3VZZmb0ZedrcUj5eXifiCM1JvlWCtfOG0zsy/th-FileID-32x32.png",
            "fileid": FileID,
            "hosts": [
                "c14.pcloud.com"
            ]
        },
        ...
    ]
}
```
