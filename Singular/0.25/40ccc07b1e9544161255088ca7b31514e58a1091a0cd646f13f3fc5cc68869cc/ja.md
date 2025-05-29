```
lift(M::smodule{T}, SM::smodule{T}, goodShape::Bool, isSB::Bool, divide::Bool) where T
```

`SM`の生成子を`M`の生成子の観点から表します。`(result, rest, U)`を返し、`Matrix(SM)*U - Matrix(rest) = Matrix(M)*Matrix(result)`が成り立ちます。もし`SM`が`M`に含まれる場合、`rest`は零モジュールです。そうでない場合、`!divide`なら`rest = SM`、`divide`なら`rest = normalform(SM, std(M))`です。`U`は単位の対角行列で、局所環の順序付けに対してのみ単位行列と異なります。

3つのブールオプションがあります。`goodShape`: `SM`の生成子の最大非零インデックスが`M`のそれ以下であること、これは`rank(SM)==rank(M)`のランクチェックから来るべきです。`isSB`: `M`の生成子がグレブナー基底を形成します。`divide`: `SM`が`M`の部分モジュールでないことを許可します。
