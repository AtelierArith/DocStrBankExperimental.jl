```
getpubaudiolink(client::PCloudClient; kwargs...)
```

公開リンクファイルのオーディオファイルへのリンクを作成します。このリンクはストリーミングに使用できます。

`code`（およびフォルダへのリンクの場合は`fileid`）で識別される公開ファイルに対して動作するため、`getaudiolink`と同じです。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubaudiolink.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか

# オプション引数

  * `fileid::Int`: 公開リンクがフォルダへのものである場合のファイルのID
  * `forcedownload::Int`: Content-Type = application/octet-streamでダウンロード
  * `contenttype::String`: Content-Typeを設定
  * `abitrate::Int`: オーディオビットレート（キロビット単位）、16から320まで
