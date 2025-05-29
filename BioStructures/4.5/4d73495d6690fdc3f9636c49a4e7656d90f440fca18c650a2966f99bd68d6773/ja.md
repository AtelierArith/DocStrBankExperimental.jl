```
downloadentirepdb(; <keyword arguments>)
```

RCSBサーバーから全てのタンパク質データバンク（PDB）をダウンロードします。

ダウンロードしたPDB IDのリストを返します。実行する前に十分なディスクスペースと時間があることを確認してください。この関数はいつでも停止でき、再度呼び出してダウンロードを再開できます。インターネット接続が必要です。

# 引数

  * `dir::AbstractString=pwd()`: PDBファイルがダウンロードされるディレクトリ; デフォルトは現在の作業ディレクトリです。
  * `format::Type=PDBFormat`: PDBファイルのフォーマット; オプションはPDBFormat、PDBXMLFormat、MMCIFFormatです。MMTFファイルはもはやダウンロードできません。
  * `overwrite::Bool=false`: `true`に設定すると、`dir`にPDBファイルが存在する場合は上書きします; デフォルトでは、PDBファイルが存在する場合はダウンロードをスキップします。
