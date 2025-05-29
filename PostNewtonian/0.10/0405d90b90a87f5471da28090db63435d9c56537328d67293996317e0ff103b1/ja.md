```
FDPNSystem{FT, PNOrder}(state, Λ₁, Λ₂)
```

`PNSystem`は、[`FastDifferentiation.jl`](https://docs.juliahub.com/General/FastDifferentiation/stable/)からの変数としての情報を含むシステムです。

この型の特定のインスタンスについては、[`fd_pnsystem`](@ref)を参照してください。この型は、最終的にこのシステムを使用する関数に渡される実際の数値の浮動小数点型である`FT`型も含まれています。`FDPNSystem`の正しい型は、`𝓔′`の計算に使用されます。
