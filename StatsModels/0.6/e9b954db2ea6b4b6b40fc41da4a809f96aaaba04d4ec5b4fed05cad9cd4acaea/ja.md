```
Term <: AbstractTerm
```

式中の変数のプレースホルダーで、型（および必要なデータ不変条件）がまだ知られていないものです。これは、[`apply_schema`](@ref)によって[`ContinuousTerm`](@ref)または[`CategoricalTerm`](@ref)に変換されます。

# フィールド

  * `sym::Symbol`: この項が参照するデータ列の名前。
