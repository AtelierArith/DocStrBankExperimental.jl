```
listrevisions(client::PCloudClient; kwargs...)
```

指定された `fileid` / `path` のリビジョンをリストします。

ソース: https://docs.pcloud.com/methods/revisions/listrevisions.html

# 引数

  * `fileid::Int`: リビジョンされたファイルのID
  * `path::String`: リビジョンされたファイルのパス

`fileid` または `path` を使用します。

# 出力

リビジョンを配列としてリストし、各要素には以下のフィールドがあります。

  * `revisionid::Int`: リビジョンのID
  * `size::Int`: 指定されたリビジョンのファイルサイズ
  * `hash::String`: ファイル内容のハッシュ（メタデータと同じ）
  * `created::datetime`: リビジョンが作成された日時

また、ファイルのメタデータも返します。
