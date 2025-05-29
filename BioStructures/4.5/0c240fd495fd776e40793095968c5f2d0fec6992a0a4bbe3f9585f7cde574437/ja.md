```
retrievepdb(pdbid::AbstractString; <keyword arguments>)
```

RCSBサーバーからタンパク質データバンク（PDB）ファイルまたは生物学的アセンブリをダウンロードして読み込み、`MolecularStructure`を返します。

インターネット接続が必要です。

# 引数

  * `pdbid::AbstractString`: ダウンロードして読み込むPDB ID。
  * `dir::AbstractString=pwd()`: PDBファイルがダウンロードされるディレクトリ; デフォルトは現在の作業ディレクトリ。
  * `format::Type=MMCIFFormat`: PDBファイルのフォーマット; オプションはPDBFormat、PDBXMLFormatおよびMMCIFFormat。MMTFファイルはもはやダウンロードできません。
  * `obsolete::Bool=false`: `true`に設定すると、指定された`dir`内の自動生成された「obsolete」ディレクトリにPDBファイルがダウンロードされます。
  * `overwrite::Bool=false`: `true`に設定すると、`dir`にPDBファイルが存在する場合は上書きします; デフォルトでは、PDBファイルが存在する場合はダウンロードをスキップします。
  * `ba_number::Integer=0`: 0より大きい場合は、対応する生物学的アセンブリをダウンロードします; デフォルトではPDBファイルをダウンロードします。
  * `structure_name::AbstractString="$pdbid.pdb"`: 返される`MolecularStructure`に付けられる名前; デフォルトはPDB ID。
  * `remove_disorder::Bool=false`: alt loc IDが' 'または'A'でない原子を削除するかどうか。
  * `read_std_atoms::Bool=true`: 標準ATOMレコードを読み込むかどうか。
  * `read_het_atoms::Bool=true`: HETATOMレコードを読み込むかどうか。
  * `run_dssp::Bool=false`: DSSPを実行して二次構造を割り当てるかどうか。`true`に設定した場合はDSSP_jll.jlパッケージをインポートする必要があります。
  * `run_stride::Bool=false`: STRIDEを実行して二次構造を割り当てるかどうか。`true`に設定した場合はSTRIDE_jll.jlパッケージをインポートする必要があります。
