The fields available in the case of the 1D deterministic solution:

  * `V`: Vector in 1D, with the solution saved at the specified time instants
  * `x`: Vector with the discretised space in direction $x$
  * `tsaved`: Time instants where the solution was saved (for auxiliary purposes)
  * `N`: Dimension of the solution at a specific time instant

## Methods available:

The domain was discretised as `x=x1,...,xN`

Solve the 1D NFE: `V = solveNFE(prob,[tj,tk,tl])`.

  * `V(tj::Float)`: Returns the solution at `tj` (vector)
  * `V(1::Int)`: Returns the solution at `tj` by referring to its index (V(tj)==V(1))
  * `V(xi::Float,tk)`: Returns 1D solution at point `xi` at `tk`
