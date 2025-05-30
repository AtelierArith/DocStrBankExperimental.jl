```
lc, mvf = example_critical_simplex(dim)
```

次元 `dim` の単体複体を作成し、すべてのセルが臨界である多重ベクトル場をその上に定義します。

この関数は、GF(2) 上のレフシェッツ複体 `lc` と多重ベクトル場 `mvf` を返します。

# 例

```jldoctest
julia> lc, mvf = example_critical_simplex(2);

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   1   1   0   0]
[0   0   0   1   0   1   0]
[0   0   0   0   1   1   0]
[0   0   0   0   0   0   1]
[0   0   0   0   0   0   1]
[0   0   0   0   0   0   1]
[0   0   0   0   0   0   0]

julia> print(cm.labels)
["A", "B", "C", "AB", "AC", "BC", "ABC"]
```
