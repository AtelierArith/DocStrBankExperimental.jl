```
add_to_expression!(expression, terms...)
```

`expression`をインプレースで`expression + (*)(terms...)`に更新します。

これは通常、右辺の項の一時的な割り当てを避けるため、`expression += (*)(terms...)`よりもはるかに効率的です。

例えば、`add_to_expression!(expression, a, b)`は`expression += a*b`と同じ結果を生成し、`add_to_expression!(expression, a)`は`expression += a`と同じ結果を生成します。

## 実装するタイミング

定義されているメソッドはごくわずかで、主に内部使用のために定義されており、以下のケースにのみ適用されます：

1. 効率的に実装できる場合
2. `expression`が結果を格納できる場合。例えば、`add_to_expression!(::AffExpr, ::GenericVariableRef, ::GenericVariableRef)`は定義されていません。なぜなら、`GenericAffExpr`は二つの変数の積を格納できないからです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> expr = 2 + x
x + 2

julia> add_to_expression!(expr, 3, x)
4 x + 2

julia> expr
4 x + 2
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> @expression(model, ex1, sum(x))
x[1] + x[2]

julia> @expression(model, ex2, 2 * sum(x))
2 x[1] + 2 x[2]

julia> add_to_expression!(ex1, ex2)
3 x[1] + 3 x[2]

julia> ex1
3 x[1] + 3 x[2]

julia> ex2
2 x[1] + 2 x[2]
```
