```
register(
    model::Model,
    op::Symbol,
    dimension::Integer,
    f::Function;
    autodiff:Bool = false,
)
```

`model`内で`dimension`引数を取るユーザー定義関数`f`をシンボル`op`として登録します。

関数`f`は、引数としてすべての`Real`のサブタイプをサポートする必要があります。入力が`Float64`であると仮定しないでください。

## 注意事項

  * このメソッドでは、ユーザー提供の勾配関数`∇f`が与えられていないため、`autodiff = true`を明示的に設定する必要があります。
  * 二次導関数情報は、`dimension == 1`の場合にのみ計算されます。
  * `op`は`f`と同じシンボルである必要はありませんが、一般的にはより読みやすくなります。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::T) where {T<:Real} = x^2
register(model, :foo, 1, f; autodiff = true)
@NLobjective(model, Min, foo(x))
```

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x[1:2])
g(x::T, y::T) where {T<:Real} = x * y
register(model, :g, 2, g; autodiff = true)
@NLobjective(model, Min, g(x[1], x[2]))
```
