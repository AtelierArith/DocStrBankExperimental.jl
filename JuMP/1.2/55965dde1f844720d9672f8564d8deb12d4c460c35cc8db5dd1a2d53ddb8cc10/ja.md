```
register(
    model::Model,
    s::Symbol,
    dimension::Integer,
    f::Function,
    ∇f::Function,
    ∇²f::Function,
)
```

ユーザー定義関数 `f` を、`model` 内の `dimension` 引数を取るシンボル `s` として登録します。さらに、勾配関数 `∇f` とヘッセ行列関数 `∇²f` を提供します。

`∇f` と `∇²f` は、それぞれ関数 `f` の1次および2次導関数に対応する数値を返さなければなりません。

## 注意事項

  * 自動微分は使用されていないため、入力はすべて `Float64` であると仮定できます。
  * `dimension > 1` の場合、このメソッドはエラーをスローします。
  * `s` は `f` と同じシンボルである必要はありませんが、一般的には同じである方が読みやすいです。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
f(x::Float64) = x^2
∇f(x::Float64) = 2 * x
∇²f(x::Float64) = 2.0
register(model, :foo, 1, f, ∇f, ∇²f)
@NLobjective(model, Min, foo(x))
```
