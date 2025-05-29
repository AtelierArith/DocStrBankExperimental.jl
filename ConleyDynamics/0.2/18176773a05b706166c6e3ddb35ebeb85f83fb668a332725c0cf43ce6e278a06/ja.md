```
lc, mvf, coords = example_three_cm(mvftype)
```

*マロゼクとワンナー*による接続行列論文の図2の例のために、単体複体と多重ベクトル場を作成します。

`mvftype`の値に応じて、周期軌道（0=デフォルト）または3つの勾配（1,2,3）のいずれかの例を返します。

この関数は、有理数体上のレフシェッツ複体`lc`と多重ベクトル場`mvf`を返します。プロット用に必要な場合、3番目の返り値`coords`は頂点の座標ベクトルを提供します。

# 例

```jldoctest
julia> lc, mvf = example_three_cm(0);

julia> cm = connection_matrix(lc, mvf);

julia> print(cm.labels)
["A", "C", "CE", "AC", "BD", "DF", "ABC", "EFG"]

julia> full_from_sparse(cm.matrix)
8×8 Matrix{Rational{Int64}}:
 0  0  0  -1  -1  0   0  0
 0  0  0   1   1  0   0  0
 0  0  0   0   0  0   0  0
 0  0  0   0   0  0  -1  0
 0  0  0   0   0  0   1  0
 0  0  0   0   0  0   0  1
 0  0  0   0   0  0   0  0
 0  0  0   0   0  0   0  0
```
