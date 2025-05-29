```
pdbentry(pdbid::AbstractString; format=MMCIFFormat, kws...)
```

キーワード引数は[`BioStructures.downloadpdb`](https://biojulia.dev/BioStructures.jl/stable/api/#BioStructures.downloadpdb-Tuple{AbstractString})に伝播されます。

ダウンロードは一時ディレクトリにキャッシュされます。

## 例

```jldoctest
julia> pdbentry("1EYE")
[ Info: PDBからファイルをダウンロード中: 1EYE
1-element ProteinStructure "1EYE.cif":
 256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE" # 便利な文字列マクロ
[ Info: ファイルは存在します: 1EYE
1-element ProteinStructure "1EYE.cif":
 256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE"A # 特定のチェーンを取得するための文字列サフィックス
[ Info: ファイルは存在します: 1EYE
256-residue ProteinChain{Float64} (A)

julia> pdb"1EYE"1 # "ba_number"キーワードを指定するための整数サフィックス
[ Info: PDBからファイルをダウンロード中: 1EYE
2-element ProteinStructure "1EYE_ba1.cif":
 256-residue ProteinChain{Float64} (A)
 256-residue ProteinChain{Float64} (A-2)
```
