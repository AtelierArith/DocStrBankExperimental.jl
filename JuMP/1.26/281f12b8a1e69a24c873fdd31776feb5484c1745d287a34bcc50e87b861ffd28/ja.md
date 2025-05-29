```
@NLobjective(model, sense, expression)
```

`model`に非線形目的を追加し、最適化の感覚`sense`を指定します。`sense`は`Max`または`Min`でなければなりません。

!!! compat
    このマクロはレガシー非線形インターフェースの一部です。[非線形モデリング](@ref)に文書化されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLobjective`を[`@objective`](@ref)に置き換えることができます。


## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @NLobjective(model, Max, 2x + 1 + sin(x))

julia> print(model)
Max 2.0 * x + 1.0 + sin(x)
Subject to
```
