```
OneHot([T = Float32])
```

One-hotエンコードは、`n`クラスとサイズ`sz`を持つ`MaskMulti`を、要素型`T`のサイズ`(sz..., n)`の配列項目に変換します。 [`apply!`](@ref)をサポートしています。

```julia
item = MaskMulti(rand(1:4, 100, 100), 1:4)
apply(OneHot(), item)
```
