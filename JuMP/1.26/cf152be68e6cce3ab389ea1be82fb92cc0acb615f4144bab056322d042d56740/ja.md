```
add_nonlinear_operator(
    model::Model,
    dim::Int,
    f::Function,
    [∇f::Function,]
    [∇²f::Function];
    [name::Symbol = Symbol(f),]
)

`dim` 入力引数を持つ新しい非線形演算子を `model` に追加し、名前 `name` に関連付けます。

関数 `f` は演算子を評価し、スカラーを返す必要があります。

オプションの関数 `∇f` は一次導関数を評価し、オプションの関数 `∇²f` は二次導関数を評価します。

`∇²f` は `∇f` が提供されている場合にのみ提供できます。

## 一変数構文

`dim == 1` の場合、各関数のメソッドシグネチャは次のようになります：

  * `f(::T)::T where {T<:Real}`
  * `∇f(::T)::T where {T<:Real}`
  * `∇²f(::T)::T where {T<:Real}`

## 多変数構文

`dim > 1` の場合、各関数のメソッドシグネチャは次のようになります：

  * `f(x::T...)::T where {T<:Real}`
  * `∇f(g::AbstractVector{T}, x::T...)::Nothing where {T<:Real}`
  * `∇²f(H::AbstractMatrix{T}, x::T...)::Nothing where {T<:Real}`

勾配ベクトル `g` とヘッセ行列 `H` はインプレースで埋められます。ヘッセ行列については、非ゼロの下三角エントリのみを埋める必要があります。オフ対角の上三角要素を設定するとエラーが発生する可能性があります。

## 例

```

jldoctest julia> model = Model();

julia> @variable(model, x) x

julia> f(x::Float64) = x^2 f (generic function with 1 method)

julia> ∇f(x::Float64) = 2 * x ∇f (generic function with 1 method)

julia> ∇²f(x::Float64) = 2.0 ∇²f (generic function with 1 method)

julia> op*f = add*nonlinear_operator(model, 1, f, ∇f, ∇²f) NonlinearOperator(f, :f)

julia> @objective(model, Min, op_f(x)) f(x)

julia> op_f(2.0) 4.0 ```
