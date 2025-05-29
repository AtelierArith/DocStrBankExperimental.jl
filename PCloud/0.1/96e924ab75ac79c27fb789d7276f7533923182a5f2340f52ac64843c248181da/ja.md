```
getpubvideolinks(client::PCloudClient; kwargs...)
```

公開リンクのビデオの異なる品質/解像度バージョンの `variants` 配列を返します。

getvideolinks と同様ですが、`code`（およびリンクがフォルダへのものである場合は `fileid`）で識別される公開ファイルで動作します。

`code` は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubvideolinks.html

# 引数

  * `code::String`: 'code' または 'shortcode' のいずれか

# オプション引数

  * `fileid::Int`: 公開リンクがフォルダへのものである場合のファイルのID
  * `forcedownload::Int`: Content-Type = application/octet-stream でダウンロード
  * `contenttype::String`: Content-Type を設定
  * `maxspeed::Int`: ダウンロード速度を制限
  * `skipfilename::Bool`: 生成されたリンクにファイル名を含める
