```
AttractorMapper(ds::DynamicalSystem, args...; kwargs...) → mapper
```

`AttractorMapper`のサブタイプは、`ds`の初期条件をアトラクタにマッピングする構造体です。見つかったアトラクタは`mapper`内に保存され、`attractors = extract_attractors(mapper)`を呼び出すことで取得できます。

現在利用可能なマッピング方法：

  * [`AttractorsViaProximity`](@ref)
  * [`AttractorsViaRecurrences`](@ref)
  * [`AttractorsViaFeaturizing`](@ref)

すべての`AttractorMapper`サブタイプは、[`basins_fractions`](@ref)または[`basins_of_attraction`](@ref)と一緒に使用できます。

さらに、一部のマッパーは初期条件の関数として呼び出すことができます：

```julia
label = mapper(u0)
```

これにより、`u0`が収束するアトラクタのラベルがその場で計算され、返されます。これが可能なマッパーは：

  * [`AttractorsViaProximity`](@ref)
  * [`AttractorsViaRecurrences`](@ref)
  * [`AttractorsViaFeaturizing`](@ref) で[`GroupViaHistogram`](@ref)の設定を使用するものです。

また、安定性測定の推定を加速するためにこのインターフェースを拡張する[`StabilityMeasuresAccumulator`](@ref)も参照してください。

## 開発者向け

`AttractorMapper`は拡張可能なインターフェースを定義します。新しいタイプは`AttractorMapper`をサブタイプ化し、[`extract_attractors`](@ref)、`id = mapper(u0)`、および内部関数`Attractors.referenced_dynamical_system(mapper)`を実装する必要があります。これらから、ライブラリの残りの部分はすべて正常に動作します！`id = mapper(u0)`を実装することが不可能な場合は、代わりに`ics`を初期条件のベクトルとして`basins_fractions(mapper, ics)`を拡張してください。
