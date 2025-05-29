```
Functional(fun)
```

The transform that applies a `fun` elementwise.

```
Functional(col₁ => fun₁, col₂ => fun₂, ..., colₙ => funₙ)
```

Apply the corresponding `funᵢ` function to each `colᵢ` column.

# Examples

```julia
Functional(exp)
Functional(log)
Functional(1 => exp, 2 => log)
Functional(:a => exp, :b => log)
Functional("a" => exp, "b" => log)
```
