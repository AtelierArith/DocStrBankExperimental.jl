```
@parse_expression(expr; operators, variable_names, node_type=Node, evaluate_on=[])
```

(Experimental) Parse a symbolic expression `expr` into a computational graph where nodes represent operations or variables.

## Arguments

  * `expr`: An expression to parse into an `AbstractExpression`.

## Keyword Arguments

  * `operators`: An instance of `AbstractOperatorEnum` specifying the available unary and binary operators.
  * `variable_names`: A list of variable names as strings or symbols that are allowed in the expression.
  * `evaluate_on`: A list of external functions to evaluate explicitly when encountered.
  * `expression_type`: The type of the resulting expression. Defaults to `Expression`.
  * `node_type`: The type of the nodes in the resulting expression tree. Defaults to `default_node_type(expression_type)`.
  * `binary_operators`: Convenience syntax for creating an `OperatorEnum`.
  * `unary_operators`: Convenience syntax for creating an `OperatorEnum`.

## Usage

The macro is used to convert a high-level symbolic expression into a structured expression tree that can be manipulated or evaluated. Here are some examples of how to use `parse_expression`:

### Parsing from a custom operator

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

### Handling expressions with symbolic variable names

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

### Using external functions and variables

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
