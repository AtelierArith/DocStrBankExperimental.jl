```
Descriptor(vos::Vector{<:Integer}, mo::Integer, pos::Vector{<:Integer}, po::Integer)::Descriptor
```

`Descriptor`を作成します。これは、`length(vos)`の変数を持ち、各変数の個別の切断順序は`vos`で指定され、`length(pos)`のパラメータを持ち、各パラメータの個別の切断順序は`pos`で指定されます。変数とパラメータの両方を含む最大切断順序は`mo`であり、単項式のパラメータ部分の切断順序は`po`です。

### 入力

  * `vos` – 各変数の個別の切断順序の`Vector`
  * `mo`  – 変数とパラメータを含むTPSAの最大切断順序
  * `pos` – 各パラメータの個別の切断順序の`Vector`
  * `po` – 単項式のパラメータ部分の切断順序
