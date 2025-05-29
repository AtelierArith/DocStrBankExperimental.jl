```
struct PolynomialDNI <: DNIMethod
```

多項式デノイジングおよび補間メソッド。

[サヴィッツキー・ゴレイフィルター](https://en.wikipedia.org/wiki/Savitzky%E2%80%93Golay_filter)と同様に動作しますが、補間も行います。

コンストラクタ:

  * `PolynomialDNI(; fields...)`

フィールド:

  * `degree::Int64`: 多項式の次数 デフォルト: (2, "length")
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`
