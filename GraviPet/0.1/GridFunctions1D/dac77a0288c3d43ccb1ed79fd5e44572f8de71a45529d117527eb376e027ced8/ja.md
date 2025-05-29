```
GridFunction1D{S,T}(name::AbstractString, domain::Interval{S}, codomain::Interval{T}, npoints::Int)
GridFunction1D(name::AbstractString, domain::Interval{S}, codomain::Interval{T}, npoints::Int)
```

ゼロ値のグリッド関数を作成します。つまり、どこでもゼロであるグリッド関数です。`codomain`は、[`Interval{T}()`](@ref)を介して作成されたゼロ値のドメインであることができます。

`npoints`はグリッド関数の解像度を指定します。これにより、他のグリッド関数を作成する際にゼロ値のグリッド関数を「テンプレート」や「スケルトン」として便利に使用できます。

このゼロ値のグリッド関数は効率的に表現されており、グリッドポイントごとに1つの要素を保存しません。
