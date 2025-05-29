```
lc1, lc2, mvf, coords1, coords2 = example_nonunique()
```

同じ単体複体を表す2つの表現と、非一意の接続行列を示す1つの多ベクトル場を作成します。

2つの複体 `lc1` と `lc2` は、GF(2) 上の同じ単体複体を表しますが、ラベルの順序が異なります。

この関数は、Lefschetz 複体 `lc1` と `lc2`、および多ベクトル場 `mvf` を返します。プロット用に必要な場合、4番目と5番目の返り値 `coords1` と `coords2` は、2つの複体の頂点の座標ベクトルを提供します。

# 例

```jldoctest
julia> lc1, lc2, mvf = example_nonunique();

julia> cm1 = connection_matrix(lc1, mvf);

julia> cm2 = connection_matrix(lc2, mvf);

julia> sparse_show(cm1.matrix)
[0   0   0   1   0   1   0   0   0]
[0   0   0   1   0   1   0   0   0]
[0   0   0   0   0   0   0   1   1]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm1.labels)
["2", "7", "79", "29", "45", "67", "168", "349", "789"]
julia> sparse_show(cm2.matrix)
[0   0   0   1   0   1   0   0   0]
[0   0   0   1   0   1   0   0   0]
[0   0   0   0   0   0   1   0   1]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   1   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm2.labels)
["2", "8", "78", "29", "45", "67", "168", "349", "789"]
```
