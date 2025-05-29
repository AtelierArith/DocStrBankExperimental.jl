```
@parse_expression(expr; operators, variable_names, node_type=Node, evaluate_on=[])
```

（実験的）シンボリックな式 `expr` を、ノードが演算または変数を表す計算グラフにパースします。

## 引数

  * `expr`: `AbstractExpression` にパースする式。

## キーワード引数

  * `operators`: 利用可能な単項および二項演算子を指定する `AbstractOperatorEnum` のインスタンス。
  * `variable_names`: 式で許可される変数名の文字列またはシンボルのリスト。
  * `evaluate_on`: 遭遇したときに明示的に評価する外部関数のリスト。
  * `expression_type`: 結果の式の型。デフォルトは `Expression`。
  * `node_type`: 結果の式木のノードの型。デフォルトは `default_node_type(expression_type)`。
  * `binary_operators`: `OperatorEnum` を作成するための便利な構文。
  * `unary_operators`: `OperatorEnum` を作成するための便利な構文。

## 使用法

このマクロは、高レベルのシンボリックな式を操作または評価できる構造化された式木に変換するために使用されます。以下は `parse_expression` の使用例です。

### カスタム演算子からのパース

```julia
julia> my_custom_op(x, y) = x + y^3;

julia> operators = OperatorEnum(binary_operators=[+, -, *, my_custom_op], unary_operators=[sin]);

julia> ex = @parse_expression my_custom_op(x, sin(y) + 0.3) operators=operators variable_names=["x", "y"]
my_custom_op(x, sin(y) + 0.3)

julia> typeof(ex)
Expression{Float64, Node{Float64}, OperatorEnum{Tuple{typeof(+), typeof(-), typeof(*), typeof(my_custom_op)}, Tuple{typeof(sin)}}, Vector{String}}

julia> typeof(ex.tree)
Node{Float64}

julia> ex(ones(2, 1))
1-element Vector{Float64}:
 2.487286478935302
```

### シンボリック変数名を持つ式の処理

```julia
julia> ex = @parse_expression(
            cos(exp(α - 1)),
            operators=OperatorEnum(binary_operators=[-], unary_operators=[cos, exp]),
            variable_names=[:α],
            node_type=GraphNode
        )
cos(exp(α))

julia> typeof(ex.tree)
GraphNode{Float32}
```

### 外部関数と変数の使用

```
julia> c = 5.0
5.0

julia> show_type(x) = (@show typeof(x); x);

julia> ex = @parse_expression(
           c * 2.5 - show_type(cos(x)),
           operators = OperatorEnum(; binary_operators=[*, -], unary_operators=[cos]),
           variable_names = [:x],
           evaluate_on = [show_type],
       )
typeof(x) = Node{Float32}
(5.0 * 2.5) - cos(x)
```
