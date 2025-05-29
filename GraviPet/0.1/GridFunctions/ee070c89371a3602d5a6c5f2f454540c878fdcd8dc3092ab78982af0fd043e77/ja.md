```
GridFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
GridFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T}, grid_size::SVector{DS,Int})
```

ゼロ値のグリッド関数を作成します。つまり、どこでもゼロであるグリッド関数です。`codomain`は、[`Box{DT,T}()`](@ref)を介して作成されたゼロ値のドメインであることができます。

`grid_size`は、グリッド関数の解像度を指定します。これにより、他のグリッド関数を作成する際にゼロ値のグリッド関数を「テンプレート」や「スケルトン」として使用するのが便利になります。

このゼロ値のグリッド関数は効率的に表現されており、グリッドポイントごとに1つの要素を保存しません。
