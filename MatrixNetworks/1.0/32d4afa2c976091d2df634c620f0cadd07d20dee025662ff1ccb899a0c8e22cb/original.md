# `seeded_pagerank`

PageRank is the stationary distribution of a Markov chain defined as follows. The behavior of the chain at state i is: 

  * with probability $lpha$, randomly transition to an out-neighbor of the current node (based on a weighted probabilities if the graph has non-negative weights).
  * with probability $1-lpha$, jump according to a distribution called the teleportation distribution and given by a vector $v$. (In the standard case, $v$ is the uniform distribution over nodes, but this is a parameter).
  * if there are no out-neighbors, then transition according to the teleportation distribution (this is the strongly-personalized problem).

When $v$ is the uniform vector, then we compute the same thing as the PageRank call itself.    

The solution satisfies a linear system of equations. This function will solve that linear system to a 1-norm error of `tol` where `tol` is chosen by default to be the machine precision. 

The solution is always a probability distribution.

## Functions

  * For any input, A can be either `A::SparseMatrixCSC{V,Int}` for some value type V or `A::MatrixNetwork{V}`
  * `x = seeded_pagerank(A,alpha::Float64,v::Float64)`
  * `x = seeded_pagerank(A,alpha::Float64,v::Int)`
  * `x = seeded_pagerank(A,alpha::Float64,v::Set{Int})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Dict{Int,Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::SparseMatrixCSC{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::SparseVector{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Vector{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Vector{Float64})`
  * `x = seeded_pagerank(A,alpha,v,eps::Float64)` specifies solution tolerance too.

## Inputs

  * `A`: The sparse matrix or matrix network that you wish to use to compute PageRank. In the case of a sparse matrix, it must have non-negative values and the values will impact the  computation as we will compute a stochastic normalization  as part of the algorithm.
  * `alpha`: the teleportation parameter given above.
  * `v`: the teleportation distribution vector. This can be an integer to teleport to a single node, a set to teleport (uniformly) to a set of nodes, a dictionary or sparse vector to weight the teleportation. Or a general dense vector.
  * `tol`: the tolerance that we solve the linear system to (this is an error guarantee)

## Examples

```
seeded_pagerank(A,alpha,5) 
            # return the seeded PageRank vector 
            # with teleportation to node 5 
            # computed to machine precision            
```
