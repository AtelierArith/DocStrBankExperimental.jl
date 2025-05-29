```
getpubthumblink(client::PCloudClient; kwargs...)
```

公開ファイルのサムネイルへのリンクを取得します

`code`（およびフォルダへのリンクの場合は`fileid`）で識別される公開ファイルに対して動作する、`getthumblink`と同じです。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubthumblink.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか
  * `fileid::Int`: サムネイルのファイルID、リンクがフォルダの場合
  * `size::String`: WIDTHxHEIGHT

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: pngに設定されている場合、サムネイルはpng形式になります
