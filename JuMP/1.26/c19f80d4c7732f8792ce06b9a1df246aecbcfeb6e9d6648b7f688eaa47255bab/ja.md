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

ユーザー定義関数 `f` を `model` 内の `dimension` 引数を取るシンボル `s` として登録します。さらに、勾配関数 `∇f` とヘッセ行列関数 `∇²f` を提供します。

`∇f` と `∇²f` は、それぞれ関数 `f` の1次および2次導関数に対応する数値を返さなければなりません。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。[非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。


## 注意事項

  * 自動微分が使用されていないため、入力はすべて `Float64` であると仮定できます。
  * `dimension > 1` の場合、このメソッドはエラーをスローします。
  * `s` は `f` と同じシンボルである必要はありませんが、一般的にはそれがより読みやすくなります。

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

julia> register(model, :foo, 1, f, ∇f, ∇²f)

julia> @NLobjective(model, Min, foo(x))

```
