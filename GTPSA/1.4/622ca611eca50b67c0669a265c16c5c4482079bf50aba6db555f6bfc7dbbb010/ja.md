```
Descriptor(vos::Vector{<:Integer}, mo::Integer)::Descriptor
```

`vos`の長さの変数を持つTPSA `Descriptor`を作成し、各変数の個別の切断順序はベクトル`vos`で指定され、TPSAの最大切断順序は`mo`です。

### 入力

  * `vos` – 各変数の個別の切断順序の`Vector`
  * `mo`  – TPSAの最大切断順序、<= sum(vos)
