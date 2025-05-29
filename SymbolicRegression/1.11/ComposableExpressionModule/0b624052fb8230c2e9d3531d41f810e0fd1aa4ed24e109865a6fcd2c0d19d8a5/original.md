```
ComposableExpression{T,N,D} <: AbstractComposableExpression{T,N} <: AbstractExpression{T,N}
```

A symbolic expression representing a mathematical formula as an expression tree (`tree::N`) with associated metadata (`metadata::Metadata{D}`). Used to construct and manipulate expressions in symbolic regression tasks.

Example:

Create variables `x1` and `x2`, and build an expression `f = x1 * sin(x2)`:

```julia
operators = OperatorEnum(; binary_operators=(+, *, /, -), unary_operators=(sin, cos))
variable_names = ["x1", "x2"]
x1 = ComposableExpression(Node(Float64; feature=1); operators, variable_names)
x2 = ComposableExpression(Node(Float64; feature=2); operators, variable_names)
f = x1 * sin(x2)
# ^This now references the first and second arguments of things passed to it:

f(x1, x1) # == x1 * sin(x1)
f(randn(5), randn(5)) # == randn(5) .* sin.(randn(5))

# You can even pass it to itself:
f(f, f) # == (x1 * sin(x2)) * sin((x1 * sin(x2)))
```
