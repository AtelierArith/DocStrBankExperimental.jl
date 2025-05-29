Calculate the two-dimensional phase diagram for the Berry phase over a specified parameter range.

```
calcPhaseDiagram(prob::BPProblem, param_range1::T1, param_range2::T2, alg::T3=BP(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:BerryPhaseAlgorithms,T4<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the Berry phase for a two-dimensional system described by `BPProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::BPProblem`:  A structure that contains the problem settings for Berry phase calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range1::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the Berry phase.
  * `param_range2::AbstractVector`: A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the Berry phase.
  * `alg::BerryPhaseAlgorithms=BP()`:  The algorithm used to compute the Berry phase. The default is `BP()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the Berry phase calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: A copy of the input `param_range1`.
      * `param2::AbstractVector`: A copy of the input `param_range2`.
      * `nums::AbstractArray`: An array containing the computed Berry phases for each parameter. The size of this array is (**number of bands** × **number of param1** × **number of param2**).

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = KitaevChain(k, p)
julia> # Set up the Berry phase problem
       prob = BPProblem(H₀)
julia> # Define a parameter range
       param1 = range(-3.0, 3.0, length=4)
       param2 = range(-1.0, 1.0, length=4)
julia> # Calculate the phase diagram (using the default BP algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param1, param2; plot=true, progress=true)
(param1 = -3.0:2.0:3.0, param2 = -1.0:0.6666666666666666:1.0, nums = [0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0;;; 0 1 1 0; 0 1 1 0])

julia> result.param1
-3.0:2.0:3.0

julia> result.param2
-1.0:0.6666666666666666:1.0

julia> result.nums
2×4×4 Array{Int64, 3}:
[:, :, 1] =
 0  1  1  0
 0  1  1  0

[:, :, 2] =
 0  1  1  0
 0  1  1  0

[:, :, 3] =
 0  1  1  0
 0  1  1  0

[:, :, 4] =
 0  1  1  0
 0  1  1  0
```
