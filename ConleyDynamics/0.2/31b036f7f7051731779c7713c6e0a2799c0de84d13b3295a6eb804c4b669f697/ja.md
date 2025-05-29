```
lc, mvf, coords = example_forman1d()
```

図1に示された*Batko, Kaczynski, Mrozek, and Wanner*によるFoCM 2020論文の例のための単体複体と多ベクトル場を作成します。

この関数は、Lefschetz複体`lc`と多ベクトル場`mvf`を返します。プロット用に必要な場合、3番目の返り値`coords`は頂点の座標ベクトルを提供します。Lefschetz複体は有限体GF(2)上で定義されています。

# 例

```jldoctest
julia> lc, mvf = example_forman1d();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   0]

julia> print(cm.labels)
["A", "AD", "F", "BF", "DE"]
```
