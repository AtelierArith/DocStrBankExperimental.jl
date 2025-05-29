```
getthumb(client::PCloudClient; kwargs...)
```

ファイルのサムネイルを取得します

getthumblinkと同じパラメータを受け取りますが、現在のAPI接続を介してサムネイルを返します。

APIサーバーからサムネイルを取得することは、ストレージサーバーから取得するよりも一般的に速くはありません。

（開くのにコストがかかる可能性のあるSSL）API接続を再利用する場合にのみ意味があります。

出典: https://docs.pcloud.com/methods/thumbnails/getthumb.html

# 引数

  * `fileid::Int`: サムネイル用のファイルのID
  * `path::String`: サムネイル用のファイルのファイルパス
  * `size::String`: WIDTHxHEIGHT

`fileid`または`path`を使用します

# オプション引数

  * `crop::Int`: 設定されている場合、サムネイルがトリミングされます
  * `type::String`: pngに設定されている場合、サムネイルはpng形式になります
