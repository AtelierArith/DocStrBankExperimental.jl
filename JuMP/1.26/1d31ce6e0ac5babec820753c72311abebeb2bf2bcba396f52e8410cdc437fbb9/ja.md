```
register(
    model::Model,
    op::Symbol,
    dimension::Integer,
    f::Function;
    autodiff:Bool = false,
)
```

`model`内の`dimension`引数を取るユーザー定義関数`f`をシンボル`op`として登録します。

関数`f`は、引数としてすべての`Real`のサブタイプをサポートする必要があります。入力が`Float64`であると仮定しないでください。

!!! compat
    この関数は、レガシー非線形インターフェースの一部です。[非線形モデリング](@ref)に文書化されている新しい非線形インターフェースの使用を検討してください。


## 注意事項

  * このメソッドでは、ユーザー提供の勾配関数`∇f`が与えられていないため、`autodiff = true`を明示的に設定する必要があります。
  * 二次導関数情報は、`dimension == 1`の場合にのみ計算されます。
  * `op`は`f`と同じシンボルである必要はありませんが、一般的にはそれがより読みやすいです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f(x::T) where {T<:Real} = x^2
f (generic function with 1 method)

julia> register(model, :foo, 1, f; autodiff = true)

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

julia> register(model, :g, 2, g; autodiff = true)

julia> @NLobjective(model, Min, g(x[1], x[2]))
```
