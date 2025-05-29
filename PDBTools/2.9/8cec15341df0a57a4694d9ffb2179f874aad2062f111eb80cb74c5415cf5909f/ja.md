```
eachsegment(atoms::AbstractVector{<:Atom})
```

選択のセグメントのイテレータ。

### 例

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> sit = eachsegment(ats)
 セグメントイテレータの長さ = 2

julia> for seg in sit
           @show length(seg)
       end
length(seg) = 1905
length(seg) = 92

julia> collect(sit)
2要素のベクター{Segment}[ 
    A-(1905 atoms))
    B-(92 atoms))
]
```
