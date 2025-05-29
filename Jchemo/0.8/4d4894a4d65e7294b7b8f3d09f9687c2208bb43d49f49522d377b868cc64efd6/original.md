```
rpmatgauss(p::Int, nlv::Int, Q = Float64)
```

Build a gaussian random projection matrix.

  * `p` : Nb. variables (attributes) to project.
  * `nlv` : Nb. of simulated projection    dimensions.
  * `Q` : Type of components of the built    projection matrix.

The function returns a random projection matrix V of  dimension `p` x `nlv`. The projection of a given matrix X  of size n x `p` is given by X * V.

V is simulated from i.i.d. N(0, 1) / sqrt(`nlv`).

## References

Li, V., Hastie, T.J., Church, K.W., 2006. Very sparse random  projections, in: Proceedings of the 12th ACM SIGKDD International  Conference on Knowledge Discovery and Data Mining, KDD ’06.  Association for Computing Machinery, New York, NY, USA, pp. 287–296.  https://doi.org/10.1145/1150402.1150436

## Examples

```julia
using Jchemo
p = 10 ; nlv = 3
rpmatgauss(p, nlv)
```
