```
lc, mvf = example_subdivision(mvftype)
```

接続行列論文の*マロゼク & ワンナー*の図11の例のために、レフシェッツ複体と多ベクトル場を作成します。

`mvftype`の値に応じて、多ベクトル（0=デフォルト）または2つの組合せベクトル場（1,2）のいずれかの例を返します。

この関数は、有理数上のレフシェッツ複体`lc`と多ベクトル場`mvf`を返します。

# 例

```jldoctest
julia> lc, mvf = example_subdivision(1);

julia> cm = connection_matrix(lc, mvf);

julia> full_from_sparse(cm.matrix)
5×5 Matrix{Rational{Int64}}:
 0  0  -1  -1  -1
 0  0   1   0   0
 0  0   0   0   0
 0  0   0   0   0
 0  0   0   0   0
```
