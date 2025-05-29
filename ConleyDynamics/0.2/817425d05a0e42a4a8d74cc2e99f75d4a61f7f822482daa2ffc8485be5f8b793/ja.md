```
lc, mvf = example_critical_simplex(dim)
```

次元 `dim` の単体複体と、そのすべてのセルが臨界である多ベクトル場を作成します。

この関数は、GF(2) 上のレフシェッツ複体 `lc` と多ベクトル場 `mvf` を返します。

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
