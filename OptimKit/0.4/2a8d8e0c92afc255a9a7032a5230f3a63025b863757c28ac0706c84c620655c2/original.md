```
optimtest(fg, x, [d]; alpha = -0.1:0.001:0.1, retract = _retract, inner = _inner)
-> αs, fs, dfs1, dfs2
```

Test the compatibility between the computation of the gradient, the retraction and the inner product by computing the derivative of the objective function along a curve corresponding to a retraction starting at the point `x` in the direction `d` in two different ways. In particular, at point `αs` which are in the middle of the points in the original range or list `alpha`, both the function value `fs` as well as the two different values for the derivative `dfs1` and `dfs2` are returned, where the derivatives are computed by

1. numerical differentation, i.e. `dfs1` contains the values `(fg(retract(x, d, alpha[i+1])[1])[1] - fg(retract(x, d, alpha[i])[1])[1])/(alpha[i+1]-alpha[i])` as an estimate for the derivative at the point `(alpha[i]+alpha[i+1])/2`
2. using the gradient, i.e. `dfs2` contains the values `inner(xα, dα, gα)` where `xα, dα = retract(x, d, α)` for values `α = (alpha[i]+alpha[i+1])/2` and `gα = fg(xα)[2]`.

It is up to the user to check that the values in `dfs1` and `dfs2` match up to expected precision, by inspecting the numerical values or plotting them. If these values don't match, the linesearch in `optimize` cannot be expected to work.
