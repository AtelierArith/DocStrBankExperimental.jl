```
モデル
```

モデルデータ構造。これはPDBファイル内のモデルのデータを保持します。モデルは`atoms`ベクター内で連続している必要があり、同じ`model`フィールドを持つことで識別されます。

Model構造体は、含まれるモデルのプロパティを保持しますが、元の原子ベクターをコピーすることはせず、モデルのメタデータと元のベクターへの参照のみを保持します。したがって、モデルの原子に対する変更は、元の原子ベクターに反映されます。

### 例

以下の例では、8S8Nは11モデルを持つPDBエントリです。

```jldoctest
julia> using PDBTools

julia> ats = wget("8S8N");

julia> models = collect(eachmodel(ats))
11-element Vector{Model}[
    1-(234 atoms))
    2-(234 atoms))
    ⋮
    10-(234 atoms))
    11-(234 atoms))
]

julia> models[1]
 Model 1 with 234 atoms.
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     DLE     A        2        1   -5.811   -0.380   -2.159  1.00  0.00     1                 1
       2   CA     DLE     A        2        1   -4.785   -0.493   -3.227  1.00  0.00     1                 2
⋮
     233  HT2   A1H5T     B      101       13   -5.695    5.959   -3.901  1.00  0.00     1               233
     234  HT1   A1H5T     B      101       13   -4.693    4.974   -2.743  1.00  0.00     1               234

```
