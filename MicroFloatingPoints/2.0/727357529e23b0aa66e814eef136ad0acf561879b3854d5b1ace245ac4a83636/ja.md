```
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Floatmu{szE,szf}) where {szE,szf}
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Float64) where {szE,szf}
FloatmuIterator(start::Floatmu{szE,szf},stop::Floatmu{szE,szf},
                step::Int = 1) where {szE,szf}
FloatmuIterator(::Type{Floatmu{szE,szf}},start::Float64,stop::Float64,
                step::Int = 1) where {szE,szf}
FloatmuIterator(::Type{Floatmu{szE,szf}},start::Float64,stop::Float64,
                step::Float64) where {szE,szf}
```

`Floatmu{szE,szf}` の範囲 `[start,stop]` 内のすべての値を生成するイテレータです。このイテレータは、2つの `Floatmu{szE,szf}` または2つの `Float64` で初期化できます。

デフォルトでは、1つの浮動小数点数から次の浮動小数点数へと繰り返すことができますが、任意のステップを選択することもできます。ステップは浮動小数点数の数であるか、加算する量である可能性があります。

境界がNaNの場合、選択したステップがゼロの場合（または `Floatmu{szE,szf}` に変換したときにゼロに丸められる場合）、またはステップが `[last, stop]` 内の2つの連続した浮動小数点数の間の最大距離よりも小さい値である場合、ArgumentErrorが発生します（許可される最小値を知るには [`eligible_step`](@ref) を使用してください）。

ステップが加算する量である場合、境界は無限大であってはなりません。

ステップが浮動小数点数の数である場合、境界には無限大が許可され、常に結果の範囲の一部となります：

```jldoctest
julia> collect(FloatmuIterator(Floatmu{2,2},-Inf,Inf,5))
6-element Vector{Floatmu{2, 2}}:
 -Infμ{2, 2}
  -1.8
  -0.5
   0.75
   2.0
  Infμ{2, 2}
```

# 例

```jldoctest
julia> L=[x for x = FloatmuIterator(Floatmu{2, 2}(0.0), Floatmu{2, 2}(1.0))]
5-element Vector{Floatmu{2, 2}}:
 0.0
 0.25
 0.5
 0.75
 1.0
julia> L2=[x for x = FloatmuIterator(Floatmu{2, 2}, 0.0, 1.0, 2)]
3-element Vector{Floatmu{2, 2}}:
 0.0
 0.5
 1.0
```
