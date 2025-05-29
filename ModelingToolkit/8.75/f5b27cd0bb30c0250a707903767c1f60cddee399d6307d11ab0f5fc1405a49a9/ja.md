```julia
struct Sample <: Symbolics.Operator
```

サンプル演算子を表します。離散時間信号は、連続時間信号をサンプリングすることによって作成されます。

# コンストラクタ

`Sample(clock::TimeDomain = InferredDiscrete())` `Sample([t], dt::Real)`

`Sample(x::Num)` は、単一の引数を持つ場合、`Sample()(x)` の短縮形です。

# フィールド

  * `clock`

# 例

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> Δ = Sample(t, 0.01)
(::Sample) (generic function with 2 methods)
```
