Calculate the first Chern numbers in the two-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
solve(prob::FCProblem, alg::T1=FHS(); parallel::T2=UseSingleThread()) where {T1<:FirstChernAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::FCProblem`: The FCProblem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=FHS()`: The algorithm to use for calculating the first Chern numbers. Default is `FHS` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `FCSolution`: A struct that contains the calculated first Chern numbers.

# Examples

```julia
julia> H(k) = Haldane(k, (1, 0.5, 1.0))
julia> prob = FCProblem(H)
julia> result = solve(prob)
FCSolution{Vector{Int64}, Int64}([1, -1], 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
  1
 -1
```
