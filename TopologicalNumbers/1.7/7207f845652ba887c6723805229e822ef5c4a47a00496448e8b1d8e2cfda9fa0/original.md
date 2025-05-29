Calculate the one-dimensional phase diagram for the first Chern number over a specified parameter range.

```
calcPhaseDiagram(prob::FCProblem, param_range::T1, alg::T2=FHS(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:FirstChernAlgorithms,T3<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the first Chern number for a one-dimensional system described by `FCProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::FCProblem`:  A structure that contains the problem settings for first Chern number calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the first Chern number.
  * `alg::FirstChernAlgorithms=FHS()`:  The algorithm used to compute the first Chern number. The default is `FHS()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the first Chern number calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: A copy of the input `param_range`.
      * `nums::AbstractMatrix`: A matrix containing the computed first Chern numbers for each parameter. The size of this matrix is (**number of bands** × **number of parameter values**).

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = Haldane(k, p)
       H(k, p) = H₀(k, (1, p, 2.5))
julia> # Set up the first Chern number problem
       prob = FCProblem(H)
julia> # Define a parameter range
       param = range(-π, π, length=10);
julia> # Calculate the phase diagram (using the default FHS algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -3.141592653589793:0.6981317007977318:3.141592653589793, nums = [0 0; -1 1; -1 1; -1 1; 0 0; 0 0; 1 -1; 1 -1; 1 -1; 0 0])

julia> result.param
-3.141592653589793:0.6981317007977318:3.141592653589793

julia> result.nums
10×2 Matrix{Int64}:
  0   0
 -1   1
 -1   1
 -1   1
  0   0
  0   0
  1  -1
  1  -1
  1  -1
  0   0
```
