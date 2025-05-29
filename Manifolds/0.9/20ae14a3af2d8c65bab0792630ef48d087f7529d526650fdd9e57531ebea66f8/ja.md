```
exp(::SymplecticGrassmann, p, X)
exp!(M::SymplecticGrassmann, q, p, X)
```

指数写像を計算します

$$
  \exp\colon T\mathrm{SpGr}(2n, 2k) → \mathrm{SpGr}(2n, 2k)
$$

点と接ベクトルをシンプレクティック基底とその接線として表現する場合、すなわち[`SymplecticStiefel`](@ref)多様体上で。次に、これを[`exp(::SymplecticStiefel, p, X)`](@ref)に渡すことができます。
