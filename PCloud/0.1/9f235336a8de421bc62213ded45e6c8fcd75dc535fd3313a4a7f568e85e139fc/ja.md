```
getpubtextfile(client::PCloudClient; kwargs...)
```

異なる文字エンコーディングでファイルをダウンロードします。このファイルは、コンテンツサーバーからこのメソッドへの応答としてストリーミングされます。

gettextfileと同様ですが、`code`（およびフォルダーへのリンクの場合は`fileid`）で識別される公開ファイルで動作します。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダーへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubtextfile.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか

# オプション引数

  * `fileid::Int`: 公開リンクがフォルダーへのものである場合のファイルのID
  * `fromencoding::String`: ファイルの元の文字エンコーディング（デフォルト: 推測）
  * `toencoding::String`: 出力の要求された文字エンコーディング（デフォルト: utf-8）
  * `forcedownload::Int`: Content-Type = application/octet-streamでダウンロード
  * `contenttype::String`: Content-Typeを設定
