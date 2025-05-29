```
getpubthumb(client::PCloudClient; kwargs...)
```

公開ファイルのサムネイルを取得

getthumbと同様ですが、`code`（およびフォルダへのリンクの場合は`fileid`）で識別される公開ファイルで動作します。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubthumb.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか
  * `fileid::Int`: サムネイル用のファイルのID（リンクがフォルダの場合）
  * `size::String`: WIDTHxHEIGHT

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: pngに設定されている場合、サムネイルはpng形式になります
