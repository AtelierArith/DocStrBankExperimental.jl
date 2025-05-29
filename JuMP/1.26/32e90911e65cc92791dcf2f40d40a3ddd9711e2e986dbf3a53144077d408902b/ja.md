```
@NLexpression(args...)
```

他の非線形制約や目的に挿入できる非線形式を効率的に構築します。 [`@expression`]も参照してください。

!!! compat
    このマクロはレガシー非線形インターフェースの一部です。 [非線形モデリング](@ref)に文書化されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLexpression`を[`@expression`](@ref)に置き換えることができます。


## 例

```jldoctest api_nlexpression
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, y)
y

julia> @NLexpression(model, my_expr, sin(x)^2 + cos(x^2))
subexpression[1]: sin(x) ^ 2.0 + cos(x ^ 2.0)

julia> @NLconstraint(model, my_expr + y >= 5)
(subexpression[1] + y) - 5.0 ≥ 0

julia> @NLobjective(model, Min, my_expr)
```

集合に対するインデクシングや匿名式もサポートされています：

```jldoctest api_nlexpression
julia> @NLexpression(model, my_expr_1[i=1:3], sin(i * x))
3-element Vector{NonlinearExpression}:
 subexpression[2]: sin(1.0 * x)
 subexpression[3]: sin(2.0 * x)
 subexpression[4]: sin(3.0 * x)

julia> my_expr_2 = @NLexpression(model, log(1 + sum(exp(my_expr_1[i]) for i in 1:2)))
subexpression[5]: log(1.0 + (exp(subexpression[2]) + exp(subexpression[3])))
```
