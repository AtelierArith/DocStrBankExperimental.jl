```
MultilinearExpression
```

Implements a multilinear expression data type as a dictionary of monoids to coefficients.

### Examples

```julia

# Creates a constant expression

@show c = MultilinearExpression(7.4)

# Creates expressions with single term

@show e1 = MultilinearExpression(4.0,1) @show e2 = MultilinearExpression(3.0,1,3) ````
