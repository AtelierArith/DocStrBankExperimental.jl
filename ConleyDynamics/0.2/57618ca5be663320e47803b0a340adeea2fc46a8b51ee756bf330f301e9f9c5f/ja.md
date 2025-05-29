```
lc, mvf = example_multiflow()
```

接続行列論文の*Mrozek & Wanner*の図3の例のために、Lefschetz複体と多ベクトル場を作成します。

この関数は、GF(2)上のLefschetz複体`lc`と多ベクトル場`mvf`を返します。

# 例

```jldoctest
julia> lc, mvf = example_multiflow();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0]
[0   0   0   0]
[0   0   0   0]
[0   0   0   0]

julia> print(cm.labels)
["BD", "DF", "AC", "CE"]
```
