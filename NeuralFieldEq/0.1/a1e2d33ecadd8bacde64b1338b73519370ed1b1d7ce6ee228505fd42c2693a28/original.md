The fields available in the case of the 1D stochastic solution:

  * `V`: Matrix `(N x np)`, where the `p-th` column corresponds to the `p-th` trajectory.
  * `meanV`: Matrix with the mean solution across all `np` trajectories
  * `x`: Vector with the discretised space in direction $x$
  * `tsaved`: Time instants where the solution was saved (auxiliary purposes)
  * `N`: Dimension of the solution at a specific time instant (auxiliary purposes)

## Methods available:

The domain was discretised as `x=x1,...,xN`

Solve the 1D SNFE: `Vsto = solveNFE(prob,[tj,tk,tl],ϵ,np)`.

  * `Vsto(tj::Float,p::Int)`: Returns the `p-th` trajectory at `tj` (vector)
  * `Vsto(tj::Float)`: Returns the mean solution at `tj` (vector)
  * `Vsto(xi,tk,p)`: Returns `p-th` trajectory at point `xi` at `tk`
  * `Vsto(xi,tk)`: Returns mean solution at point `xi` at `tk`
