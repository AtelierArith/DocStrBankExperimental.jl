```
getpubzip(client::PCloudClient; kwargs...)
```

公開リンクファイルのzipアーカイブファイルを作成し、ダウンロードします

getzipと同様ですが、`code`（およびフォルダへのリンクの場合は`fileid`）で識別される公開ファイルで動作します。

`code`を取得するには、次のコマンドを使用します：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンク`filename`、`forcedownload`、および`timeoffset`のオプションパラメータは、getzipと同様に機能します。

ソース: https://docs.pcloud.com/methods/public_links/getpubzip.html

# 引数

  * `code::String`: 'code'または'shortcode'のいずれか

# オプション引数

  * `forcedownload::Int`: 設定されている場合、content-typeは'application/octet-stream'になります。設定されていない場合は'application/zip'になります。
  * `filename::String`: 提供されている場合、これは'Content-Disposition'ヘッダーとして返され、ブラウザがファイルをダウンロードする際にこのファイル名を採用するよう強制します。ファイル名は変更されずに渡されるため、.zip拡張子を含める必要があります。
  * `timeoffset::String`: 希望する時間オフセット

# 出力

成功した場合、要求されたツリー内のすべてのファイルとディレクトリを含むzipアーカイブが現在のAPI接続を介して返されます。
