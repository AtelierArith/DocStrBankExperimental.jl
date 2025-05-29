```
polyfeatures(x,order)
```

Compute monomial features up to a certain degree. For instance, if the input consists in vectors in ℝ², then the monomials of degree ≤ 2 are 1,x₁,x₂,x₁x₂,x₁²,x₂² Note that the number of monomials of degree r in dimension d equals ${ d+r \choose r}$

If the input points are in d > 1, indicate whether the input x is d * n or n * d using ColVecs or RowVecs.

The output has points along rows and monomials along columns.

## Examples

```
x = randn(2,10) #10 points in dim 2
polyfeatures(ColVecs(x),2) #Output has 10 rows and 6 column
polyfeatures(RowVecs(x),2) #Output has 2 rows and 66 columns

```
