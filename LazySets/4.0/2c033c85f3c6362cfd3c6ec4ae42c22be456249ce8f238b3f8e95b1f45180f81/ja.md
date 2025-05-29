```
AbstractAffineMap{N, S<:LazySet{N}} <: LazySet{N}
```

アフィンマップのための抽象型。

### 注意事項

このインターフェースの標準実装については[`AffineMap`](@ref)を参照してください。

すべての具体的な`AbstractAffineMap`は、以下のメソッドを定義する必要があります：

  * `matrix(::AbstractAffineMap)` – 線形マップを返す
  * `vector(::AbstractAffineMap)` – アフィン変換ベクトルを返す
  * `set(::AbstractAffineMap)` – マップが適用される集合を返す

`AbstractAffineMap`のサブタイプ：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractAffineMap)
7-element Vector{Any}:
 AffineMap
 ExponentialMap
 ExponentialProjectionMap
 InverseLinearMap
 LinearMap
 ResetMap
 Translation
```
