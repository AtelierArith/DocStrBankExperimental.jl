```
StructuredExpression{T,F,N,E,TS,D} <: AbstractStructuredExpression{T,F,N,E,D} <: AbstractExpression{T,N}
```

This expression type allows you to combine multiple expressions together in a predefined way.

# Parameters

  * `T`: The numeric value type of the expressions.
  * `F`: The type of the structure function, which combines each expression into a single expression.
  * `N`: The type of the nodes inside expressions.
  * `E`: The type of the expressions.
  * `TS`: The type of the named tuple containing those inner expressions.
  * `D`: The type of the metadata, another named tuple.

# Usage

For example, we can create two expressions, `f`, and `g`, and then combine them together in a new expression, `f_plus_g`, using a constructor function that simply adds them together:

```julia
kws = (;
    binary_operators=[+, -, *, /],
    unary_operators=[-, cos, exp],
    variable_names=["x", "y"],
)
f = parse_expression(:(x * x - cos(2.5f0 * y + -0.5f0)); kws...)
g = parse_expression(:(exp(-(y * y))); kws...)

f_plus_g = StructuredExpression((; f, g); structure=nt -> nt.f + nt.g)
```

Now, when evaluating `f_plus_g`, this expression type will return the result of adding together the results of `f` and `g`.

You can dispatch on a particular structured expression with the second type parameter, `F`, which is the function defined above:

```julia
my_factory(nt) = nt.f + nt.g

Base.show(io::IO, e::StructuredExpression{T,typeof(my_factory)}) where {T} = ...
```

which will create a new method particular to this expression type defined on that function.
