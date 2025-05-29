```
AverageVectorFieldMethod([T=Rational{Int}])
```

Construct a representation of the average vector field (AVF) method using coefficients of type `T`. You can pass it as argument to [`bseries`](@ref) to construct the corresponding B-series.

# Examples

We can generate this as follows.

```jldoctest
julia> series = bseries(AverageVectorFieldMethod(), 3)
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 5 entries:
  RootedTree{Int64}: Int64[]   => 1
  RootedTree{Int64}: [1]       => 1
  RootedTree{Int64}: [1, 2]    => 1//2
  RootedTree{Int64}: [1, 2, 3] => 1//4
  RootedTree{Int64}: [1, 2, 2] => 1//3
```

# References

The B-series of the average vector field (AVF) method is given by $b(.) = 1$ and $b([t_1, ..., t_n]) = b(t_1)...b(t_n) / (n + 1)$, see

  * Elena Celledoni, Robert I. McLachlan, David I. McLaren, Brynjulf Owren, G. Reinout W. Quispel, and William M. Wright. "Energy-preserving Runge-Kutta methods." ESAIM: Mathematical Modelling and Numerical Analysis 43, no. 4 (2009): 645-649. [DOI: 10.1051/m2an/2009020](https://doi.org/10.1051/m2an/2009020)
