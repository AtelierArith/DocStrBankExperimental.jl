```
セグメント
```

セグメントデータ構造。セグメントは`atoms`ベクター内で連続している必要があり、同じ`segname`および`model`フィールドを持つことで識別されます。

セグメント構造体は、含まれているセグメントのプロパティを保持しますが、元の原子ベクターをコピーすることはせず、セグメントのメタデータと元のベクターへの参照のみを保持します。したがって、セグメントの原子に対する変更は、元の原子ベクターに反映されます。

### 例

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> segments = collect(eachsegment(ats))
2-element Vector{Segment}[
    A-(1905 atoms))
    B-(92 atoms))
]

julia> segname.(segments[1:2])
2-element Vector{InlineStrings.String7}:
 "A"
 "B"

julia> length(segments[2])
92

```
