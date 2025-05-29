```
FunctionTerm{F,Args} <: AbstractTerm
```

Julia関数への呼び出しを表します。最初の型パラメータはキャプチャされた関数の型（例：`typeof(log)`）であり、2番目はキャプチャされた引数の型（例：`AbstractTerm`の`Vector`）です。

ネストされた関数呼び出しは、さらに`FunctionTerm`としてキャプチャされます。

# フィールド

  * `f::F`: キャプチャされた関数（例：`log`）
  * `args::Args`: `@formula`に渡された呼び出しの引数で、各々が`AbstractTerm`としてキャプチャされます。通常、これは`Vector{<:AbstractTerm}`です。
  * `exorig::Expr`: `@formula`に渡された元の式

# 型パラメータ

  * `F`: キャプチャされた関数の型（例：`typeof(log)`）
  * `Args`: キャプチャされた引数のコンテナの型。

# 例

```jldoctest
julia> f = @formula(y ~ log(1 + a + b))
FormulaTerm
Response:
  y(unknown)
Predictors:
  (a,b)->log(1 + a + b)

julia> typeof(f.rhs)
FunctionTerm{typeof(log), Vector{FunctionTerm{typeof(+), Vector{AbstractTerm}}}}

julia> typeof(only(f.rhs.args))
FunctionTerm{typeof(+), Vector{AbstractTerm}}

julia> only(f.rhs.args).args
3-element Vector{AbstractTerm}:
 1
 a(unknown)
 b(unknown)

julia> f.rhs.f(1 + 3 + 4)
2.0794415416798357

julia> modelcols(f.rhs, (a=3, b=4))
2.0794415416798357

julia> modelcols(f.rhs, (a=[3, 4], b=[4, 5]))
2-element Vector{Float64}:
 2.0794415416798357
 2.302585092994046
```
