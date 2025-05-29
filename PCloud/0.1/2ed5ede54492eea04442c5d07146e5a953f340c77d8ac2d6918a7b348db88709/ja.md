```
gettextfile(client::PCloudClient; kwargs...)
```

異なる文字エンコーディングでファイルをダウンロードします。`fileid`（または`path`）をパラメータとして受け取り、異なる文字エンコーディングでファイルの内容を返します。ファイルはコンテンツサーバーからこのメソッドへの応答としてストリーミングされます。

オプションのパラメータ`fromencoding`は、ファイルの元の文字エンコーディングを指定します。省略した場合、ファイルの内容に基づいて推測されます。

オプションのパラメータ`toencoding`は、出力のために要求される文字エンコーディングを指定します。デフォルトは`utf-8`です。

オプションのパラメータ`forcedownload`が設定されている場合、ファイルはサーバーによってコンテンツタイプ`application/octet-stream`で提供され、通常はユーザーエージェントにファイルを保存させることを強制します。

また、サーバーに送信してほしいContent-Typeを指定するために`contenttype`パラメータを提供することもできます。これらのパラメータが設定されていない場合、コンテンツタイプはファイルの拡張子に依存します。

出典: https://docs.pcloud.com/methods/streaming/gettextfile.html

# 引数

  * `fileid::Int`: リネームされたファイルのID
  * `path::String`: リネームされたファイルへのパス

fileidまたはpathを使用

# オプションの引数

  * `fromencoding::String`: ファイルの元の文字エンコーディング（デフォルト: 推測）
  * `toencoding::String`: 出力の要求された文字エンコーディング（デフォルト: utf-8）
  * `forcedownload::Int`: Content-Type = application/octet-streamでダウンロード
  * `contenttype::String`: Content-Typeを設定

# 出力

成功した場合、このメソッドはAPIサーバーによってデータを出力します。コンテンツサーバーへのリンクは提供されません。`fromecoding`または`toencoding`に無効なエンコーディングを提供しない限り、このメソッドが失敗することはないと安全に仮定できます。
