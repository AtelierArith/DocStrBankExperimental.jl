```
lift(M::sideal{T}, SM::sideal{T}, goodShape::Bool, isSB::Bool, divide::Bool) where T
```

`SM`の生成子を`M`の生成子の観点から表します。`(result, rest, U)`を返します。`Matrix(SM)*U - Matrix(rest) = Matrix(M)*Matrix(result)`。もし`SM`が`M`に含まれている場合、`rest`は零モジュールです。そうでない場合、`rest = SM`（`!divide`の場合）、および`rest = normalform(SM, std(M))`（`divide`の場合）です。`U`は単位の対角行列で、局所環の順序に対してのみ単位行列と異なります。

3つのブールオプションがあります。`goodShape`: `SM`の生成子の最大非零インデックスが`M`のそれ以下であること、これはランクチェック`rank(SM)==rank(M)`から来るべきです。`isSB`: `M`の生成子がグレブナー基底を形成します。`divide`: `SM`が`M`の部分モジュールでないことを許可し、これは余り付きの除算に役立ちます。
