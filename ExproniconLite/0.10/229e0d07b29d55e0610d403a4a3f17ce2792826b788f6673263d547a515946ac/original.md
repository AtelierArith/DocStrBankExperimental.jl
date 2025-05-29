```
JLCall(ex::Expr)
```

Convert a Julia call expression to `JLCall`.

# Examples

```julia
ex = :(f(x, y; z=1))
jlcall = JLCall(ex)  # creates JLCall with func=:f, args=[:x, :y], kwargs=[:(z=1)]
```
