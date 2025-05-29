```
TemplateExpression{T,F,N,E,TS,D} <: AbstractExpression{T,N}
```

A symbolic expression that allows the combination of multiple sub-expressions in a structured way, with constraints on variable usage.

`TemplateExpression` is designed for symbolic regression tasks where domain-specific knowledge or constraints must be imposed on the model's structure.

# Constructor

  * `TemplateExpression(trees; structure, operators, variable_names)`

      * `trees`: A `NamedTuple` holding the sub-expressions (e.g., `f = Expression(...)`, `g = Expression(...)`).
      * `structure`: A `TemplateStructure` which holds functions that define how the sub-expressions are combined   in different contexts.
      * `operators`: An `OperatorEnum` that defines the allowed operators for the sub-expressions.
      * `variable_names`: An optional `Vector` of `String` that defines the names of the variables in the dataset.

# Example

Let's create an example `TemplateExpression` that combines two sub-expressions `f(x1, x2)` and `g(x3)`:

```julia
# Define operators and variable names
options = Options(; binary_operators=(+, *, /, -), unary_operators=(sin, cos))
operators = options.operators
variable_names = ["x1", "x2", "x3"]

# Create sub-expressions
x1 = Expression(Node{Float64}(; feature=1); operators, variable_names)
x2 = Expression(Node{Float64}(; feature=2); operators, variable_names)
x3 = Expression(Node{Float64}(; feature=3); operators, variable_names)

# Create TemplateExpression
example_expr = (; f=x1, g=x3)
st_expr = TemplateExpression(
    example_expr;
    structure=TemplateStructure{(:f, :g)}(
        ((; f, g), (x1, x2, x3)) -> sin(f(x1, x2)) + g(x3)^2
    ),
    operators,
    variable_names,
)
```

When fitting a model in SymbolicRegression.jl, you can provide `expression_spec=TemplateExpressionSpec(; structure=TemplateStructure(...))` as an option. The `variable_constraints` will constraint `f` to only have access to `x1` and `x2`, and `g` to only have access to `x3`.
