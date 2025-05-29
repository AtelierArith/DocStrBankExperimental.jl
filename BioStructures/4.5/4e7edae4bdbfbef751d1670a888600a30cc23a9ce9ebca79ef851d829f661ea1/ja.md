```
downloadpdb(pdbid::AbstractString; <keyword arguments>)
downloadpdb(pdbid::AbstractArray{<:AbstractString, 1}; <keyword arguments>)
downloadpdb(f::Function, args...)
```

RCSBを介してタンパク質データバンク（PDB）からファイルをダウンロードします。

`AbstractString`（例: `"1AKE"`）が与えられた場合、PDBファイルをダウンロードし、ファイルへのパスを返します。`Array{<:AbstractString, 1}`が与えられた場合、配列内のPDBファイルをダウンロードし、ファイルへのパスの配列を返します。最初の引数として関数が与えられた場合、ダウンロードしたファイルパスを引数として関数を実行し、その後ファイルを削除します。インターネット接続が必要です。

# 引数

  * `dir::AbstractString=pwd()`: PDBファイルがダウンロードされるディレクトリ; デフォルトは現在の作業ディレクトリです。
  * `format::Type=PDBFormat`: PDBファイルのフォーマット; オプションはPDBFormat、PDBXMLFormat、MMCIFFormatです。MMTFファイルはもはやダウンロードできません。
  * `obsolete::Bool=false`: `true`に設定すると、PDBファイルは指定された`dir`内の自動生成された「obsolete」ディレクトリにダウンロードされます。
  * `overwrite::Bool=false`: `true`に設定すると、`dir`にPDBファイルが存在する場合は上書きします; デフォルトでは、PDBファイルが存在する場合はダウンロードをスキップします。
  * `ba_number::Integer=0`: 0より大きい場合は、対応する生物学的アセンブリをダウンロードします; デフォルトではPDBファイルをダウンロードします。
