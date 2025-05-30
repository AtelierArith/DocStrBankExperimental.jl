```
register(
    model::Model,
    s::Symbol,
    dimension::Integer,
    f::Function,
    ∇f::Function;
    autodiff:Bool = false,
)
```

ユーザー定義関数 `f` を `model` 内の `dimension` 引数を取るシンボル `s` として登録します。さらに、勾配関数 `∇f` を提供します。

関数 `f` と `∇f` は、引数としてすべての `Real` のサブタイプをサポートする必要があります。入力が `Float64` であると仮定しないでください。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。[非線形モデリング](@ref) に文書化されている新しい非線形インターフェースの使用を検討してください。


## 注意事項

  * 関数 `f` が単変数の場合（すなわち、`dimension == 1`）、`∇f` は関数 `f` の一階導関数を表す数値を返さなければなりません。
  * 関数 `f` が多変数の場合、`∇f` は `∇f(g::AbstractVector{T}, args::T...) where {T<:Real}` というシグネチャを持つ必要があり、最初の引数は勾配でインプレースに修正されるベクトル `g` です。
  * `autodiff = true` で `dimension == 1` の場合、自動微分を使用して二階導関数情報を計算します。`autodiff = false` の場合、一階導関数情報のみが使用されます。
  * `s` は `f` と同じシンボルである必要はありませんが、一般的にはそれがより読みやすいです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f(x::T) where {T<:Real} = x^2
f (generic function with 1 method)

julia> ∇f(x::T) where {T<:Real} = 2 * x
∇f (generic function with 1 method)

julia> register(model, :foo, 1, f, ∇f; autodiff = true)

julia> @NLobjective(model, Min, foo(x))
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> g(x::T, y::T) where {T<:Real} = x * y
g (generic function with 1 method)

julia> function ∇g(g::AbstractVector{T}, x::T, y::T) where {T<:Real}
           g[1] = y
           g[2] = x
           return
       end
∇g (generic function with 1 method)

julia> register(model, :g, 2, g, ∇g)

julia> @NLobjective(model, Min, g(x[1], x[2]))
```
