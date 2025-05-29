## `pagerank`

PageRank is the stationary distribution of a Markov chain defined as follows. The behavior of the chain at state i is: 

  * with probability $lpha$, randomly transition to an out-neighbor of the current node (based on a weighted probabilities if the graph has non-negative weights).
  * with probability $1-lpha$, jump to a random node chosen anywhere in the network.
  * if there are no out-neighbors, then jump anywhere in the network  with equal probability.

The solution satisfies a linear system of equations. This function will solve that linear system to a 1-norm error of `tol` where `tol` is chosen by default to be the machine precision. 

The solution is always a probability distribution.        

## Functions

  * `x = pagerank(A::SparseMatrixCSC{V,Int},alpha::Float64)`
  * `x = pagerank(A::MatrixNetwork{V},alpha::Float64)`
  * `x = pagerank(A,alpha,eps::Float64)` specifies solution tolerance too.

## Inputs

  * `A`: The sparse matrix or matrix network that you wish to use to compute PageRank. In the case of a sparse matrix, it must have non-negative values and the values will impact the  computation as we will compute a stochastic normalization  as part of the algorithm.
  * `alpha`: the teleportation parameter given above.
  * `tol`: the tolerance, the default choice is machine precision  for floating point, which is more than enough for almost all  applications.

## Examples

```
pagerank(A,alpha) 
            # return the standard PageRank vector 
            # with uniform teleportation and alpha=0.85 
            # computed to machine precision            
```
