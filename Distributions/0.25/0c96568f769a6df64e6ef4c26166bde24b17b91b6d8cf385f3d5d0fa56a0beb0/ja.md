```
pdf(d::Distribution{ArrayLikeVariate{N}}, x::AbstractArray{<:Real,N}) where {N}
```

`d`の確率密度関数を`x`で評価します。

この関数は、`x`のサイズが分布`d`と互換性があるかどうかをチェックします。このチェックは`@inbounds`を使用することで無効にできます。

# 実装

`pdf`の代わりに、`x`のサイズをチェックする必要がない`_pdf(d, x)`を実装するべきです。しかし、`pdf(d, x)`のデフォルト定義は通常`logpdf(d, x)`にフォールバックするため、`logpdf`を実装するだけで十分です。

参照: [`logpdf`](@ref).
