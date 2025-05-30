```
lc, mvf = example_julia_logo()
```

接続行列論文の図1の例のための単体複体と多ベクトル場を作成します。*Mrozek & Wanner*による。

この関数は、GF(2)上のレフシェッツ複体`lc`と多ベクトル場`mvf`を返します。

# 例

```jldoctest
julia> lc, mvf = example_julia_logo();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0]
[0   0   1]
[0   0   0]

julia> print(cm.labels)
["D", "AC", "ABC"]
```
