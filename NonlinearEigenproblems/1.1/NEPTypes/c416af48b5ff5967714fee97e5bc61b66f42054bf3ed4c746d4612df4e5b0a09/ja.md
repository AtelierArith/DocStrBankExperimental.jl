```
interpolate([T=ComplexF64,] nep::NEP, intpoints::Array)
```

`intpoints`の点でNEPを補間し、[`PEP`](@ref)、すなわちモノミアル基底における多項式固有値問題を返します。チェビシェフ補間については[`ChebPEP`](@ref)を参照してください。オプション引数`T`は、PEPの行列が定義される型です。

他に[`ChebPEP`](@ref)も参照してください。
