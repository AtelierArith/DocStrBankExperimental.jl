```
read(filepath::AbstractString, format::Type; <keyword arguments>)
read(input::IO, format::Type; <keyword arguments>)
```

PDB（Protein Data Bank）ファイルを読み込み、`MolecularStructure`を返します。

# 引数

  * `format::Type`: PDBファイルのフォーマット; オプションはPDBFormat、MMCIFFormat、MMTFFormatです。MMTFFormatを使用するには、MMTF.jlパッケージをインポートする必要があります。
  * `structure_name::AbstractString`: 返される`MolecularStructure`に付けられる名前; デフォルトはファイル名です。
  * `remove_disorder::Bool=false`: alt loc IDが' 'または'A'でない原子を削除するかどうか。
  * `read_std_atoms::Bool=true`: 標準ATOMレコードを読み込むかどうか。
  * `read_het_atoms::Bool=true`: HETATOMレコードを読み込むかどうか。
  * `run_dssp::Bool=false`: DSSPを実行して二次構造を割り当てるかどうか。`true`に設定した場合、DSSP_jll.jlパッケージをインポートする必要があります。
  * `run_stride::Bool=false`: STRIDEを実行して二次構造を割り当てるかどうか。`true`に設定した場合、STRIDE_jll.jlパッケージをインポートする必要があります。
  * `gzip::Bool=false`: 入力がgzippedかどうか、PDBフォーマットでは使用できません。
