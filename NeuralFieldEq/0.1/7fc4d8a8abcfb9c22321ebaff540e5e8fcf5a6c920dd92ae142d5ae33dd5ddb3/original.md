The fields available in the case of the 2D stochastic solution:

  * `V`: 3-dimensional array `(N x (N x tsaved) x np)`, where submatrix `N x N` corresponds

to the `p-th` trajectory at `tsaved` instant

  * `meanV`: Matrix with the mean solution across all `np` trajectories
  * `x`: Vector with the discretised space in direction $x$
  * `y`: Vector with the discretised space in direction $y$
  * `tsaved`: Time instants where the solution was saved (auxiliary purposes)
  * `N`: Matrix of size N x N (auxiliary purposes).

## Methods available:

The domain was discretised as `x=x1,...,xN` and `y=y1,...,yN`.

Solve the 2D SNFE: `Vsto = solveNFE(prob,[tj,tk,tl],ϵ,np)`.

  * `Vsto(tj::Float,p::Int)`: Returns the `p-th` trajectory at `tj` (matrix)
  * `Vsto(tj::Float)`: Returns the mean solution at `tj` (matrix)
  * `Vsto(xi,yj,tk,p)`: Returns `p-th` trajectory at point `(xi,yj)` at `tk`
  * `Vsto(xi,yj,tk)`: Returns mean solution at point `(xi,yj)` at `tk`
