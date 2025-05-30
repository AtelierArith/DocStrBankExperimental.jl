```
@operator(model, operator, dim, f[, ∇f[, ∇²f]])
```

非線形演算子 `operator` を `model` に `dim` 引数で追加し、現在のスコープに `operator` という名前の新しい [`NonlinearOperator`](@ref) オブジェクトを作成します。

関数 `f` は演算子を評価し、スカラーを返す必要があります。

オプションの関数 `∇f` は一次導関数を評価し、オプションの関数 `∇²f` は二次導関数を評価します。

`∇²f` は `∇f` が提供されている場合にのみ提供できます。

## 一変数構文

`dim == 1` の場合、各関数のメソッドシグネチャは次のようにする必要があります：

  * `f(::T)::T where {T<:Real}`
  * `∇f(::T)::T where {T<:Real}`
  * `∇²f(::T)::T where {T<:Real}`

## 多変数構文

`dim > 1` の場合、各関数のメソッドシグネチャは次のようにする必要があります：

  * `f(x::T...)::T where {T<:Real}`
  * `∇f(g::AbstractVector{T}, x::T...)::Nothing where {T<:Real}`
  * `∇²f(H::AbstractMatrix{T}, x::T...)::Nothing where {T<:Real}`

勾配ベクトル `g` とヘッセ行列 `H` はインプレースで埋められます。ヘッセ行列については、非ゼロの下三角エントリのみを埋める必要があります。オフ対角の上三角要素を設定するとエラーが発生する可能性があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f(x::Float64) = x^2
f (generic function with 1 method)

julia> ∇f(x::Float64) = 2 * x
∇f (generic function with 1 method)

julia> ∇²f(x::Float64) = 2.0
∇²f (generic function with 1 method)

julia> @operator(model, op_f, 1, f, ∇f, ∇²f)
NonlinearOperator(f, :op_f)

julia> @objective(model, Min, op_f(x))
op_f(x)

julia> op_f(2.0)
4.0

julia> model[:op_f]
NonlinearOperator(f, :op_f)

julia> model[:op_f](x)
op_f(x)
```

## 非マクロ版

このマクロは、JuMP マクロの残りのスタイルに一致する便利な構文として提供されています。ただし、[`add_nonlinear_operator`](@ref) を使用してマクロの外で演算子を追加することもできます。例えば：

```jldoctest
julia> model = Model();

julia> f(x) = x^2
f (generic function with 1 method)

julia> @operator(model, op_f, 1, f)
NonlinearOperator(f, :op_f)
```

は次のように等価です：

```jldoctest
julia> model = Model();

julia> f(x) = x^2
f (generic function with 1 method)

julia> op_f = model[:op_f] = add_nonlinear_operator(model, 1, f; name = :op_f)
NonlinearOperator(f, :op_f)
```
