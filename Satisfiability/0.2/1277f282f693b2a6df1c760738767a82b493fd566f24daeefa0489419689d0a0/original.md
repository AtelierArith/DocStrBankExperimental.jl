```
@satvariable(z, Bool)
@satvariable(a[1:n], Int)
@satvariable(b, BitVector, 32)
```

Construct a SAT variable with name z, optional array dimensions, and specified type (`Bool`, `Int`, `Real` or `BitVector`). Note that some  require an optional third parameter.

One and two-dimensional arrays of variables can be constructed with the following syntax. The result will be a native Julia array.

```julia
@satvariable(a[1:n], Int) # an Int vector of length n
@satvariable(x[1:m, 1:n], Real) # an m x n Int matrix
```
