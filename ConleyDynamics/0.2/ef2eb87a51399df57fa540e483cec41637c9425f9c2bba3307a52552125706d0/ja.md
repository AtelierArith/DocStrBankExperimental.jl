```
lc1, lc2, mvf = example_small_periodicity()
```

接続行列論文の図4の例に対して、Lefschetz複体と多重ベクトル場の2つの表現を作成します。*Mrozek & Wanner*による。

複体 `lc1` と `lc2` は同じ複体の2つの表現ですが、異なる接続行列を導きます。両方のLefschetz複体は有限体GF(2)上で定義されています。

この関数は、Lefschetz複体 `lc1` と `lc2`、および多重ベクトル場 `mvf` を返します。

# 例

```jldoctest
julia> lc1, lc2, mvf = example_small_periodicity();

julia> cm1 = connection_matrix(lc1, mvf);

julia> cm2 = connection_matrix(lc2, mvf);

julia> full_from_sparse(cm1.matrix)
4×4 Matrix{Int64}:
 0  0  0  0
 0  0  0  1
 0  0  0  1
 0  0  0  0

julia> print(cm1.labels)
["A", "a", "b", "alpha"]

julia> full_from_sparse(cm2.matrix)
4×4 Matrix{Int64}:
 0  0  0  0
 0  0  0  0
 0  0  0  1
 0  0  0  0

julia> print(cm2.labels)
["A", "c", "b", "alpha"]
```
