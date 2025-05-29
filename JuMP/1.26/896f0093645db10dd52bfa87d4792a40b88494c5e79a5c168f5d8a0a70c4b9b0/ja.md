```
NonlinearOperator(func::Function, head::Symbol)
```

`head`という名前の関数を表す呼び出し可能な構造体（ファンクタ）。

[`AbstractJuMPScalar`](@ref)で呼び出されると、この構造体は[`GenericNonlinearExpr`](@ref)を返します。

非JuMP型で呼び出されると、この構造体は`func(args...)`の評価を返します。

`head`が最適化ツールによって特別扱いされない限り、演算子はすでに[`add_nonlinear_operator`](@ref)または[`@operator`](@ref)を使用してモデルに追加されている必要があります。

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

julia> bar = NonlinearOperator(f, :op_f)
NonlinearOperator(f, :op_f)

julia> @objective(model, Min, bar(x))
op_f(x)

julia> bar(2.0)
4.0
```
