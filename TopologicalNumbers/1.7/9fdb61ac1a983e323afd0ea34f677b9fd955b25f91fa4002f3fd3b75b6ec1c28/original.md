Calculate the one-dimensional phase diagram for the Berry phase over a specified parameter range.

```
calcPhaseDiagram(prob::BPProblem, param_range::T1, alg::T2=BP(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:BerryPhaseAlgorithms,T3<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the Berry phase for a one-dimensional system described by `BPProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::BPProblem`:  A structure that contains the problem settings for Berry phase calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the Berry phase.
  * `alg::BerryPhaseAlgorithms=BP()`:  The algorithm used to compute the Berry phase. The default is `BP()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the Berry phase calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: A copy of the input `param_range`.
      * `nums::AbstractMatrix`: A matrix containing the computed Berry phases for each parameter. The size of this matrix is (**number of bands** × **number of parameter values**).

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = SSH(k, p)
julia> # Set up the Berry phase problem
       prob = BPProblem(H₀)
julia> # Define a parameter range from -2.0 to 2.0 with 9 divisions
       param_range = range(-2.0, 2.0, length=9)
julia> # Calculate the phase diagram (using the default BP algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param_range; plot=true, progress=true)
(param = -2.0:0.5:2.0, nums = [1 1; 1 1; 0 0; 0 0; 0 0; 0 0; 0 0; 1 1; 1 1])

julia> result.param
-2.0:0.5:2.0

julia> result.nums
9×2 Matrix{Int64}:
 1  1
 1  1
 0  0
 0  0
 0  0
 0  0
 0  0
 1  1
 1  1
```
