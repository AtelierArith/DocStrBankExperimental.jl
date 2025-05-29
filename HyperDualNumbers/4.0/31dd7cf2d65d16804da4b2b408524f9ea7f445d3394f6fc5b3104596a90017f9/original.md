Symbolic derivative list

The format is a list of (Symbol,Expr,Expr) tuples.

Entries in each tuple:

```julia
* `:f `     : Function symbol
* `:df`    : Symbolic expression for first derivative
* `:d²f`   : Symbolic expression for second derivative
```

The symbol :x is used within deriv_expr for the point at which the derivative should be evaluated.

### Example of a tuple in the list

```julia
(:sqrt, :(1/2/sqrt(x)), :(-1/4/x^(3/2)))
```
