```
savethumb(client::PCloudClient; kwargs...)
```

ファイルのサムネイルを作成し、現在のユーザーのファイルシステムに保存します。

`topath` または `tofolderid` + `toname` に加えて、`getthumblink` と同じパラメータを受け取り、生成されたサムネイルをファイルとして保存します。

通常通り、この呼び出しは既存のファイルを上書きします（古いものをリビジョンとして保存）が、`noover` パラメータが設定されている場合は、その場合に「ファイルまたはフォルダはすでに存在します。」というエラーが生成されます。

`toname` が提供されていないが `tofolderid` がある場合、ファイルの元の名前がサムネイルに使用されます。

同様に、`topath` がスラッシュ ('/') で終わる場合、元のファイル名が追加されます。

出典: https://docs.pcloud.com/methods/thumbnails/savethumb.html

# 引数

  * `fileid::Int`: サムネイル用のファイルのID
  * `path::String`: サムネイル用のファイルのファイルパス
  * `size::String`: WIDTHxHEIGHT
  * `topath::String`: サムネイルを保存するファイルパス
  * `tofolderid::Int`: サムネイルを保存するフォルダのID
  * `toname::String`: サムネイルを保存するファイル名

`fileid` または `path` を使用

`topath` または `tofolderid` + `toname` を使用

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: png に設定されている場合、サムネイルは png 形式になります
  * `noover::Int`: 設定されている場合、上書き時にエラーが発生します

# 出力

成功した場合、`metadata`、`width`、および `height` を返します。

# 出力例

```
{
    result: 0,
    height: 32,
    width: 32,
    metadata: {
        path: "/my%20 thumb.jpg",
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
