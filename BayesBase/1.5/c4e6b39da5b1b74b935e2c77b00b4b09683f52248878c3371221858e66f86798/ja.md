```
CountingReal
```

`CountingReal` は、別のフィールドで「無限」をカウントする実数の「数」を実装しています。 [`BayesBase.Infinity`](@ref) および [`BayesBase.MinusInfinity`](@ref) も参照してください。

# 引数

  * `value::T`: 型 `<: Real` の値
  * `infinities::Int`: 追加または減算された無限の数

```jldoctest
julia> r = BayesBase.CountingReal(0.0, 0)
CountingReal{Float64}(0.0, 0)

julia> float(r)
0.0

julia> r = r + BayesBase.Infinity(Float64)
CountingReal{Float64}(0.0, 1)

julia> float(r)
Inf

julia> r = r + BayesBase.MinusInfinity(Float64)
CountingReal{Float64}(0.0, 0)

julia> float(r)
0.0
```
