```
sc, vfG, vfC = example_dunce_chaos()
```

ダンス帽の最小単体複体表現と2つのフォーマンベクトル場を作成します。

この関数は、有限体 `GF(2)` 上の `sc` にダンス帽の単体表現を返します。フォーマンベクトル場 `vfG` は、ユニークな接続行列を持つ勾配ベクトル場です。フィールド `vfC` は、このフィールドの修正であり、次元1および2の臨界セルをフォーマン矢印に統合します。結果として得られるフォーマンベクトル場はもはや勾配ではなく、実際にはローレズのような混沌を示します。

# 例

```jldoctest
julia> sc, vfG, vfC = example_dunce_chaos();

julia> homology(sc)
3-element Vector{Int64}:
 1
 0
 0

julia> cmG = connection_matrix(sc, vfG);

julia> sparse_show(cmG.matrix)
[0   0   0]
[0   0   1]
[0   0   0]

julia> print(cmG.labels)
["1", "12", "128"]

julia> cmC = connection_matrix(sc, vfC);

julia> sparse_show(cmC.matrix)
[0]

julia> print(cmC.labels)
["1"]

julia> msC, psC = morse_sets(sc, vfC, poset=true);

julia> [conley_index(sc, mset) for mset in msC]
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 0, 0]

julia> psC
2×2 Matrix{Bool}:
 0  1
 0  0

julia> msC
2-element Vector{Vector{String}}:
 ["1"]
 ["12", "14", "15", "25", "28", "56", "68", "78", "124", "125", "128", "145", "256", "278", "568", "678"]
```
