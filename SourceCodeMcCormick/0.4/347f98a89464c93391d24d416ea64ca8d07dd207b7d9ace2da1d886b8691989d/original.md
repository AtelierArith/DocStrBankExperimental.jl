```
shrink_eqs(::Vector{Equation})
shrink_eqs(::Vector{Equation}, ::Int)
```

Given a set of symbolic equations, progressively substitute the RHS definitions of LHS terms until there are only a set number of equations remaining (default = 4).

# Example

```
eqs = [y ~ 15*x,
       z ~ (1+y)^2]
shrink_eqs(eqs, 1)

1-element Vector{Equation}:
 z ~ (1 + 15x)^2
```
