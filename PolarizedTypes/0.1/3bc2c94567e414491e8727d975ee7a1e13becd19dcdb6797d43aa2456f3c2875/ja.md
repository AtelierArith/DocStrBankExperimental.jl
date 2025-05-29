```
CoherencyMatrix(s::StokesParams, basis1::PolBasis)
CoherencyMatrix(s::StokesParams, basis1::PolBasis, basis2::PolBasis)
CoherencyMatrix(s::StokesParams, basis1::PolBasis, basis2::PolBasis, refbasis=CirBasis())
```

ストークスパラメータ `s` のセットからコヒーレンシーマトリックスを構築します。これは、テンソル積基底 `|basis1><basis2|` を形成する `basis1` と `basis2` に特化しています。単一の基底が与えられた場合は、`|basis><basis|` によって構築されます。

例えば

```julia
CoherencyMatrix(s, CircBasis())
```

はコヒーレンシーマトリックスを返します

```
   I+V   Q+iU
   Q-iU  I-V
```

一方、

```julia
CoherencyMatrix(s, LinBasis())
```

は次のようになります

```
    I+Q   U+iV
    U-iV  I-Q
```

# 注意事項

内部的にこの関数はまず参照基底に変換し、次に最終基底に変換します。オプション引数 `refbasis` を使用して、使用する参照基底を選択できます。デフォルトでは、円形基底を参照として使用します。これは、`basis1` と `basis2` が異なる場合にのみ重要です。`basis1==basis2` の場合、参照基底は決して使用されません。
