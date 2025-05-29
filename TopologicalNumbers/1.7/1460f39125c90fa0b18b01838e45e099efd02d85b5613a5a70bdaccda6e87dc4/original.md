Calculate the $\mathbb{Z}_2$ numbers in the two-dimensional case with reference to Shiozaki method [Fukui2007Quantum,Shiozaki2023discrete](@cite).

```
solve(prob::Z2Problem, alg::T1=Shio(); parallel::T2=UseSingleThread()) where {T1<:Z2Algorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::Z2Problem`: The Z2Problem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=Shio()`: The algorithm to use for calculating the Z2 numbers. Default is `Shio` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `Z2Solution`: A struct that contains the calculated Z2 numbers.

# Examples

```julia
julia> H(k) = KaneMele(k, 1.0)
julia> prob = Z2Problem(H)
julia> result = solve(prob)
Z2Solution{Vector{Int64}, Nothing, Int64}([1, 1], nothing, 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
 1
 1
```
