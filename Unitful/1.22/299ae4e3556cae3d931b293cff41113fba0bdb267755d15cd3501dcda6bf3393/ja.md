```
upreferred(x::Number)
upreferred(x::Quantity)
```

`x`を`x`の次元に対して好ましい単位に単位変換します。ファクトリのデフォルトを使用している場合、この関数は基本SI単位の累乗の積に単位変換します。量`x`が[`Unitful.ContextUnits`](@ref)`(y,z)`を持つ場合、結果の量は単位`ContextUnits(z,z)`を持ちます。
