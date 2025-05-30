```
pseudo_divrem(f::_APL{S}, g::_APL{T}, algo) where {S,T}
```

`f`を`g`で割ったときの擬似商と余りを、[Knu14, Algorithm R, p. 425]で定義されているように返します。

係数の型が体でない場合、割り算を行うことが常に可能であるとは限りません。たとえば、`f = 3x + 1`を`g = 2x + 1`で割ることは整数の範囲ではできません。一方で、`2f = 3g - 1`と書くことはできます。一般に、`f`を`g`で割ったときの*擬似*割り算は次のようになります：

$$
l f(x) = q(x) g(x) + r(x)
$$

ここで、`l`は`g`の先頭係数のべき乗であり、いくつかの定数です。

[`pseudo_rem`](@ref)も参照してください。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
