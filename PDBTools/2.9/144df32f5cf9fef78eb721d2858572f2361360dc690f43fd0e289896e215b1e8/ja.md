```
eachmodel(atoms::AbstractVector{<:Atom})
```

選択のモデルのイテレータ。

### 例

ここでは、PDBファイルのモデルを反復処理し、各モデルの最初の原子のインデックスを注釈し、すべてのモデルを収集する方法を示します。

```jldoctest
julia> using PDBTools

julia> ats = wget("8S8N");

julia> models = eachmodel(ats)
 モデルイテレータの長さ = 11

julia> first_atom = Atom[]
       for model in models
           push!(first_atom, model[1])
       end
       @show index.(first_atom);
index.(first_atom) = Int32[1, 235, 469, 703, 937, 1171, 1405, 1639, 1873, 2107, 2341]

julia> collect(models)
11-element Vector{Model}[
    1-(234 atoms))
    2-(234 atoms))
    ⋮
    10-(234 atoms))
    11-(234 atoms))
]
```
