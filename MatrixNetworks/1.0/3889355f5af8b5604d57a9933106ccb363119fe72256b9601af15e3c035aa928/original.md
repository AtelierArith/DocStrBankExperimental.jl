# `seeded_stochastic_heat_kernel`

Compute the stochastic heat kernel, the result of $x = \exp(-t(I - P)) s $ where $s$ is a stochastic seed vector and $t$ is a time parameter and $P$ is a column-stochastic or sub-stochastic matrix. 

This function will return a vector $x$ such that $ \| x - x*{\mbox{exact}} \|*1 \le $ `eps`, and this function further guarantees  $x_{\mbox{exact}} - x \ge 0$.

## Functions

  * The input A can be either a `A::SparseMatrixCSC{V,Int}` or `A::MatrixNetwork{V}` for some value type `V`
  * `seeded_stochastic_heat_kernel(A,t::Float64,s)` provides the stochastic seed `s` in any of the following forms:
  * `seeded_stochastic_heat_kernel(A,t,s::Float64)`: s must be the number 1/size(A,1) and this corresponds to using the all-ones vector.
  * `seeded_stochastic_heat_kernel(A,t,s::Int)` use the vector with just a single non-zero
  * `seeded_stochastic_heat_kernel(A,t,s::Set{Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::Dict{Int,Float64})`
  * `seeded_stochastic_heat_kernel(A,t,s::SparseMatrixCSC{Float64,Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::SparseVector{Float64,Int})`
  * `seeded_stochastic_heat_kernel(A,t,s::Vector{Float64})`
  * `seeded_stochastic_heat_kernel(A,t::Float64,s,eps::Float64)`: specifies  the solution tolerance (default `eps=eps(Float64)`)

## Inputs

-`A`: A sparse matrix with non-negative entries or a matrix network object  -`t`: the value of time in the heat kernel $0 <= t$ -`eps`: the solution tolerance $ 0 < eps < 1 $ -`s`: the stochastic seed vector, this will be normalized to be stochastic

## Returns

-`x`: the result of the stochastic heat kernel evaluation

## Examples

```

```
