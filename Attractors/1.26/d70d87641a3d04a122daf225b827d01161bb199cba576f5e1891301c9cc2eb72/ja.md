```
convergence_time(mapper::AttractorMapper) → t
```

`mapper`がアトラクタに収束するのにかかったおおよその時間を返します。この関数は、`u0`が関心のある初期条件である`mapper(u0)`が呼び出された直後に呼び出す必要があります。したがって、この構文をサポートする`AttractorMapper`のサブタイプに対してのみ有効です。

収束時間を取得することは計算コストがかからないため、[`convergence_and_basins_fractions`](@ref)は常に[`basins_fractions`](@ref)の代わりに使用できます。
