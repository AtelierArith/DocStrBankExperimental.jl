The fields available in the case of the 2D deterministic solution:

  * `V`: Matrix with the solution saved at the specified time instants
  * `x`: Vector with the discretised space in direction $x$
  * `y`: Vector with the discretised space in direction $y$
  * `tsaved`: Time instants where the solution was saved (auxiliary purposes)
  * `N`: Matrix of size N x N (auxiliary purposes).

## Methods available:

The domain was discretised as `x=x1,...,xN` and `y=y1,...,yN`.

Solve the 2D NFE: `V = solveNFE(prob,[tj,tk,tl])`.

  * `V(tj::Float)`: Returns the solution at `tj` (matrix)
  * `V(1::Int)`: Returns the solution at `tj` by referring to its index (V(tj)==V(1))
  * `V(xi::Float,yj::Float,tk)`: Returns solution at point `(xi,yj)` at `tk`
