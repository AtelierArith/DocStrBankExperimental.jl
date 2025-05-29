```
register(
    model::Model,
    s::Symbol,
    dimension::Integer,
    f::Function,
    ∇f::Function;
    autodiff::Bool = false,
)
```

ユーザー定義関数 `f` を `model` 内でシンボル `s` として `dimension` 引数を取るように登録します。さらに、勾配関数 `∇f` を提供します。

関数 `f` と `∇f` は、引数としてすべての `Real` のサブタイプをサポートする必要があります。入力が `Float64` であると仮定しないでください。

## 注意事項

  * 関数 `f` が単変数の場合（すなわち、`dimension == 1`）、`∇f` は関数 `f` の一階導関数を表す数値を返さなければなりません。
  * 関数 `f` が多変数の場合、`∇f` は `∇f(g::AbstractVector{T}, args::T...) where {T<:Real}` というシグネチャを持つ必要があり、最初の引数は勾配でインプレースで修正されるベクトル `g` です。
  * `autodiff = true` で `dimension == 1` の場合、自動微分を使用して二階導関数情報を計算します。`autodiff = false` の場合、一階導関数情報のみが使用されます。
  * `s` は `f` と同じシンボルである必要はありませんが、一般的には同じである方が読みやすいです。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::T) where {T<:Real} = x^2
∇f(x::T) where {T<:Real} = 2 * x
register(model, :foo, 1, f, ∇f; autodiff = true)
@NLobjective(model, Min, foo(x))
```

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x[1:2])
g(x::T, y::T) where {T<:Real} = x * y
function ∇g(g::AbstractVector{T}, x::T, y::T) where {T<:Real}
    g[1] = y
    g[2] = x
    return
end
register(model, :g, 2, g, ∇g; autodiff = true)
@NLobjective(model, Min, g(x[1], x[2]))
```
