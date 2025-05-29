```
getpubziplink(client::PCloudClient; kwargs...)
```

公開リンクファイルのzipアーカイブファイルへのリンクを作成します

`code`で識別された公開ファイルに対して動作するため、getziplinkと同じですが、遅く、効率が悪く、zipファイルを生成するのに時間がかかります。前者はすぐにダウンロードを開始します。

`code`とオプションのパラメータを受け取り、ツリーを定義し、zipファイルをストリームします。

`code`は次の方法から取得できます: getfilepublink - 単一ファイルへのリンク getfolderpublink - フォルダへのリンク gettreepublink - ツリーへのリンク getcollectionpublink - コレクションへのリンク

出典: https://docs.pcloud.com/methods/public_links/getpubziplink.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか

# オプションの引数

  * `forcedownload::Int`: 設定されている場合、content-typeは'application/octet-stream'になります。設定されていない場合は'application/zip'になります。
  * `filename::String`: 提供されている場合、これは'Content-Disposition'ヘッダーとして返され、ブラウザがファイルをダウンロードする際にこのファイル名を採用するよう強制します。ファイル名は変更されずに渡されるため、.zip拡張子を含める必要があります。
  * `timeoffset::String`: 希望する時間オフセット
