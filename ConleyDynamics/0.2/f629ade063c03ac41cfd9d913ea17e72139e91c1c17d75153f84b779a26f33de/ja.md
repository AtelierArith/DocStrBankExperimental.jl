```
lc, mvf, coords = example_forman2d()
```

図3に示された例のための単体複体と多ベクトル場を作成します。これは*Batko, Kaczynski, Mrozek, and Wanner*によるFoCM 2020年の論文からのものです。

この関数は、有限体GF(2)上のLefschetz複体`lc`と多ベクトル場`mvf`を返します。プロット用に必要な場合、3番目の返り値`coords`は頂点の座標ベクトルを提供します。

# 例

```jldoctest
julia> lc, mvf = example_forman2d();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0   1   0   1   0   0]
[0   0   0   0   0   1   0   0   0]
[0   0   0   0   1   1   1   0   0]
[0   0   0   0   0   0   0   0   1]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   1   0]
[0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   0]

julia> print(cm.labels)
["D", "E", "F", "GJ", "BF", "EF", "HI", "ADE", "FGJ"]
```
