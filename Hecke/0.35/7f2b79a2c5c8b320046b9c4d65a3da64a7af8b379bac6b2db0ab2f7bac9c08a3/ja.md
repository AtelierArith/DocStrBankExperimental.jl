```
==(K::KodairaSymbol, s::String) -> Bool
```

Kが文字列で与えられたKodaira記号に対応する場合はtrueを返します。有効な入力は次のとおりです：I0、II、III、IVおよびIn（nは正の整数）、I0*、II*、III*、IV*およびIn*（nは正の整数）。

整数の代わりにnを代入する代わりに、一般的な型'In'または'In*'に対してチェックして、Kodaira記号がそのタイプであるかどうかをテストすることもできます。
