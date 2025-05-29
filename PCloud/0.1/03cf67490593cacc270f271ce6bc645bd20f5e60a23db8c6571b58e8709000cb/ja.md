```
savepubzip(client::PCloudClient; kwargs...)
```

現在のユーザーファイルシステムにおける公開リンクファイルのzipアーカイブファイルを作成します。

`code`によって識別される公開ファイルで動作するが、`savezip`と同じです。

`code`と、ツリーを定義するためのオプションのパラメータを受け取り、zipファイルをストリームします。

`code`は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダーへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/savepubzip.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか

# オプションの引数

  * `timeoffset::String`: 希望する時間オフセット
  * `topath::String`: zipアーカイブを保存するパス
  * `tofolderid::Int`: zipアーカイブを保存するフォルダーのID
  * `toname::String`: 希望するzipアーカイブのファイル名

# 出力

成功した場合、zipアーカイブを作成し、その`metadata`を返します。
