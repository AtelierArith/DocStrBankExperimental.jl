```
poincaresos(ds::CoupledODEs, plane, T = 1000.0; kwargs...) → P::StateSpaceSet
```

`ds`のPoincaré断面上の反復を`plane`で返し、`T`まで`ds`を進めます。断面上の点の[`StateSpaceSet`](@ref)を返します。

この関数は[`PoincareMap`](@ref)を初期化し、その[`current_crossing_time`](@ref)が`T`を超えるまでステップを進めます。また、[`PoincareMap`](@ref)とともに[`trajectory`](@ref)を使用して、`N::Int`点のシーケンスを取得することもできます。

キーワード`Ttr, save_idxs`は[`trajectory`](@ref)と同様に機能します。`plane`およびその他のすべてのキーワードについては[`PoincareMap`](@ref)を参照してください。
