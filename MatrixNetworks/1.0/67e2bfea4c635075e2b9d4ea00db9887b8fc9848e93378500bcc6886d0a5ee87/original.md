## `pagerank_power!`

**Expert interface**

This function computes the strongly personalized PageRank vector of a column sub-stochastic matrix P.

This is a powerful internal function and you most likely don't want  to use it unless you know what you are doing.  

This call is duck-typed so that it can work with arbitrary input matrix types as well as arbitrary vectors v. This enables it to be efficient in the case of sparse or dense vectors v.

The solution returned will satisfy the strongly-personalized PageRank equation to the given tolerance accuracy in the 1-norm. Formally, it'll 

This call allocates no extra memory and only uses the memory included with the vectors x and y. 

## Functions

  * `pagerank_power!{T<Float}!(x::Vector{T}, y::Vector{T},        P, alpha::T, v, tol::T, maxiter::Int, iterfunc::Function)`

## Inputs

  * `x`: a vector (of length n, where there are n nodes of the graph) that will store
  * `y`: a vector that is used as part of the matrix-vector multiplication and the iteration procedure. It is just extra memory.
  * `P`: a duck typed matrix to apply the stochastic operator     the type P must support P*x and P*y
  * `alpha`: the teleportation parameter, alpha must be between 0 and 1. This is the probability that the model follows the graph (so the problem is hard when alpha is close to 1).
  * `v`: a duck typed vector to apply the personalization       the type v must support x += v where x is a Vector{T}       examples of v include a scalar, a sparsevec, or a Vector{T}
  * `tol`: the solution tolerance in the error 1-norm.
  * `maxiter`: the maximum number of iterations
  * `iterfunc`: a function that will be called on each iteration

## Returns

  * `x`: The PageRank vector (just another reference to the input x)

## Example

```

```
