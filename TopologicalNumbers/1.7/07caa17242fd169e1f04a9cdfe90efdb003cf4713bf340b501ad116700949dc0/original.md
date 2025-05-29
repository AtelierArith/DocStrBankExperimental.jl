Calculate the winding numbers in the one-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
solve(prob::BPProblem, alg::T1=BP(); parallel::T2=UseSingleThread()) where {T1<:BerryPhaseAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::BPProblem`: The BPProblem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=BP()`: The algorithm to use for calculating the Berry phases. Default is `BP` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `BPSolution`: A struct that contains the calculated Berry phases.

# Examples

```julia
julia> H(k) = SSH(k, 1.1)
julia> prob = BPProblem(H)
julia> result = solve(prob)
BPSolution{Vector{Int64}, Int64}([1, 1], 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
 1
 1
```
