Calculate the second Chern numbers in the four-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern,Mochol-Grzelak2018Efficient](@cite).

```
solve(prob::SCProblem, alg::T1=FHS2(); parallel::T2=UseSingleThread()) where {T1<:SecondChernAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::SCProblem`: The SCProblem struct that contains the Hamiltonian matrix function in the wave number space, filling number, mesh numbers, and other parameters.
  * `alg::T1=FHS2()`: The algorithm to use for calculating the second Chern numbers. Default is `FHS2` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `SCSolution`: A struct that contains the calculated second Chern numbers.

# Examples

```julia
julia> H(k) = LatticeDirac(k, -3.0)
julia> prob = SCProblem(H)
julia> result = solve(prob)
SCSolution{Float64}(0.9793607631927381)
julia> result.TopologicalNumber
0.9793607631927381
```
