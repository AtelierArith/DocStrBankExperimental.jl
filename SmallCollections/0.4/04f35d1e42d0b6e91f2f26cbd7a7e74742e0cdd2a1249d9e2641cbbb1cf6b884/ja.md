```
SmallCollections.MapStyle

MapStyle(f, types::Type...) -> MapStyle
```

`MapStyle`は、`SmallCollections`が関数`f`を引数として受け取る`map`や`findfirst`のような特定の関数をどのように評価するかを決定します。利用可能な`MapStyle`のサブタイプは、効率が低いものから高いものまで次の通りです：

  * `LazyStyle`: 関数`f`は必要な場合にのみ評価され、デフォルト値に対して定義されているとは仮定されません。これは未知の関数に対するデフォルトの`MapStyle`です。
  * `EagerStyle`: `f`は厳密に必要な場合よりも多く評価される可能性があり、デフォルト値に対して定義されていると仮定されます。ただし、デフォルト値をデフォルト値にマッピングする必要はありません。
  * `RigidStyle`: `f`は厳密に必要な場合よりも多く評価される可能性があります。デフォルト値に対して定義されていると仮定され、すべての引数がデフォルト値である場合にはデフォルト値を返すと仮定されます。
  * `StrictStyle`: `f`は厳密に必要な場合よりも多く評価される可能性があります。デフォルト値に対して定義されていると仮定され、少なくとも1つの引数がデフォルト値である場合にはデフォルト値を返すと仮定されます。（これは、単一の引数を持つ関数に対しては`RigidStyle`と同じです。）

`MapStyle`は、`Base`の多くの関数や古い関数から新しい関数を生成する操作に対して事前定義されています。無名関数は認識されません。ただし、`SmallCollections`のいくつかの関数では、キーワード引数として`MapStyle`を指定することができます。さらに、ユーザーは自分の型に対して`MapStyle`を定義することができます。

[`SmallCollections.default`](@ref)や[`SmallCollections.isfasttype`](@ref)も参照してください。

# 例

```jldoctest
julia> using SmallCollections: MapStyle

julia> MapStyle(iszero, Int)   # not RigidStyle: iszero(0) is true, not false
SmallCollections.EagerStyle()

julia> MapStyle(+, Int, Int)
SmallCollections.RigidStyle()

julia> MapStyle(*, Int, Float64)   # not StrictStyle: 0 * Inf is NaN, not 0.0
SmallCollections.RigidStyle()

julia> MapStyle(*, Int, Int)
SmallCollections.StrictStyle()

julia> MapStyle(-, Int)
SmallCollections.StrictStyle()

julia> MapStyle(x -> -x, Int)   # not StrictStyle: anonymous function not recognized
SmallCollections.LazyStyle()

julia> MapStyle(-, Int128)   # Int128 is not a fast type, so better be lazy
SmallCollections.LazyStyle()

julia> MapStyle(isfinite∘inv, Float64)   # function composition is recognized
SmallCollections.EagerStyle()

julia> MapStyle(!iszero, Int)   # function composition again
SmallCollections.EagerStyle()

julia> MapStyle(>=(1), Int)   # >=(1) is Base.Fix2(>=, 1), which is recognized
SmallCollections.EagerStyle()
```
