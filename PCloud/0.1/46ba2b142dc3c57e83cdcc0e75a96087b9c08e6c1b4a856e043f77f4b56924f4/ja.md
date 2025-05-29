```
savepubthumb(client::PCloudClient; kwargs...)
```

パブリックリンクファイルのサムネイルを作成し、現在のユーザーのファイルシステムに保存します。

`savethumb`と同様ですが、`code`（およびフォルダへのリンクの場合は`fileid`）で識別されるパブリックファイルで動作します。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/savepubthumb.html

# 引数

  * `code::String`: 'code'または'shortcode'
  * `fileid::Int`: サムネイル用のファイルのID（リンクがフォルダの場合）
  * `size::String`: WIDTHxHEIGHT
  * `topath::String`: サムネイルを保存するファイルパス
  * `tofolderid::Int`: サムネイルを保存するフォルダのID
  * `toname::String`: サムネイルを保存するファイル名

`fileid`または`path`を使用

`topath`または`tofolderid`+`toname`を使用

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: pngに設定されている場合、サムネイルはpng形式になります
  * `noover::Int`: 設定されている場合、上書き時にエラーが発生します
