```
partition_problem(a::Vector{Float64}; num_layers::Int=1, driver=X)
```

Wrapper function setting up an instance of the partition problem.

### Input

  * `a::Vector{Float64}`: The input vector of numbers to be partitioned.
  * `num_layers::Int=1` (optional): The number of QAOA layers usually denoted by $p$.
  * `driver=X` (optional): The driver or mixer used in the QAOA.

### Output

  * An instance of the `Problem` struct holding all relevant quantities.

### Notes

The partition problem for a set of uniformly distributed numbers $\mathcal{S} = \{a_1, ..., a_N\}$  consists of finding two subsets $\mathcal{S}_{1} \cup \mathcal{S}_2 =  \mathcal{S}$  such that the difference of the sums over the two subsets $\mathcal{S}_{1, 2}$ is as small as possible.  The cost function in Ising form can be defined as 

$\hat C = -\left(\sum_{i=1}^{N} a_i \hat{Z}_i\right)^2 = \sum_{i<j\leq N} J_{ij} \hat{Z}_i \hat{Z}_j + \mathrm{const.}$

with $J_{ij}=-2a_i a_j$. The goal is then to *maximize* $\hat C$.
