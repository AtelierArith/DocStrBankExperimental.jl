```
downloadallobsoletepdb(; <keyword arguments>)
```

RCSBサーバーからすべての廃止されたProtein Data Bank (PDB)ファイルをダウンロードします。

ダウンロードしたPDB IDのリストを返します。インターネット接続が必要です。

# 引数

  * `obsolete_dir::AbstractString=pwd()`: PDBファイルがダウンロードされるディレクトリ; デフォルトは現在の作業ディレクトリです。
  * `format::Type=PDBFormat`: PDBファイルのフォーマット; オプションはPDBFormat、PDBXMLFormat、MMCIFFormatです。MMTFファイルはもはやダウンロードできません。
  * `overwrite::Bool=false`: `true`に設定すると、`dir`にPDBファイルが存在する場合に上書きします; デフォルトでは、PDBファイルが存在する場合はダウンロードをスキップします。
