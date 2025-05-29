Calculate the one-dimensional phase diagram for the second Chern number over a specified parameter range.

```
calcPhaseDiagram(prob::SCProblem, param_range::T1, alg::T2=FHS2(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:SecondChernAlgorithms,T3<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the second Chern number for a one-dimensional system described by `SCProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::SCProblem`:  A structure that contains the problem settings for second Chern number calculations, including the Hamiltonian, mesh size, number of filled bands, gap information, and other parameters. The default is a half-filled band case.
  * `param_range::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the second Chern number.
  * `alg::SecondChernAlgorithms=FHS2()`:  The algorithm used to compute the second Chern number. The default is `FHS2()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly.
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: A copy of the input `param_range`.
      * `nums::AbstractVector`: A vector containing the computed second Chern numbers for each parameter.

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = LatticeDirac(k, p)
julia> N = 10; # number of k-points in each direction
julia> # Set up the second Chern number problem
       prob = SCProblem(H₀, N)
julia> # Define a parameter range
       param = range(-4.9, 4.9, length=4)
julia> # Calculate the phase diagram (using the default FHS2 algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -4.9:3.2666666666666666:4.9, nums = [0.0010237313095167136, -2.0667333080974726, 2.1572606447321445, -0.0009805850180973081])

julia> result.param
-4.9:3.2666666666666666:4.9

julia> result.nums
4-element Vector{Float64}:
  0.0010237313095167136
 -2.0667333080974726
  2.1572606447321445
 -0.0009805850180973081
```
