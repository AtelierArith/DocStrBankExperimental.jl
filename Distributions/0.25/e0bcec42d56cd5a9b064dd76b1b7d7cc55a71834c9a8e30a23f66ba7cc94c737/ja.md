```
logpdf(d::Distribution{ArrayLikeVariate{N}}, x::AbstractArray{<:Real,N}) where {N}
```

`d`の確率密度関数の対数を`x`で評価します。

この関数は、`x`のサイズが分布`d`と互換性があるかどうかをチェックします。このチェックは`@inbounds`を使用することで無効にできます。

# 実装

`logpdf`の代わりに、`x`のサイズをチェックする必要がない`_logpdf(d, x)`を実装するべきです。

参照: [`pdf`](@ref), [`gradlogpdf`](@ref).
