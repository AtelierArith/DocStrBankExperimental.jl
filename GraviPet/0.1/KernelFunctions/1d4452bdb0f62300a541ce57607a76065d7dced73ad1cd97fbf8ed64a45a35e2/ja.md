```
KernelFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
KernelFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
```

ゼロ値のカーネル関数を作成します。すなわち、どこでもゼロであるカーネル関数です。`codomain`は、[`Box{DT,T}()`](@ref)を介して作成されたゼロ値のドメインであることができます。

`grid_size`はカーネル関数の解像度を指定します。これにより、他のカーネル関数を作成する際にゼロ値のカーネル関数を「テンプレート」や「スケルトン」として使用するのが便利になります。
