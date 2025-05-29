```
wget(PDBid; selection; format="mmCIF")
```

タンパク質データバンクからPDBファイルを取得します。選択を適用することができます。

オプションのformat引数は、"mmCIF"または"PDB"のいずれかにすることができます。デフォルトは"mmCIF"です。大きな構造のデータをダウンロードするには、"mmCIF"形式を使用することをお勧めします。

### 例

```jldoctest
julia> using PDBTools

julia> protein = wget("1LBD","chain A")
   Vector{Atom{Nothing}} with 1870 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     SER     A      225        1   45.228   84.358   70.638  1.00 67.05     1                 1
       2   CA     SER     A      225        1   46.080   83.165   70.327  1.00 68.73     1                 2
⋮
    1869  CG2     THR     A      462      238  -27.063   71.965   49.222  1.00 78.62     1              1869
    1870  OXT     THR     A      462      238  -25.379   71.816   51.613  1.00 84.35     1              1870

```
