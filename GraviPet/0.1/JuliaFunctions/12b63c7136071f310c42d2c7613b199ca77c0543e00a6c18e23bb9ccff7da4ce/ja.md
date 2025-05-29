```
JuliaFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T})
JuliaFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T})
```

ゼロ値のジュリア関数を作成します。すなわち、どこでもゼロであるジュリア関数です。`codomain`は、[`Box{DT,T}()`](@ref)を介して作成されたゼロ値のドメインであることができます。
