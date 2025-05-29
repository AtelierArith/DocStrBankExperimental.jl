Calculate the two-dimensional phase diagram for the first Chern number over a specified parameter range.

```
calcPhaseDiagram(prob::FCProblem, param_range1::T1, param_range2::T2, alg::T3=FHS(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:FirstChernAlgorithms,T4<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the first Chern number for a two-dimensional system described by `FCProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::FCProblem`:  A structure that contains the problem settings for first Chern number calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range1::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the first Chern number.
  * `param_range2::AbstractVector`: A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the first Chern number.
  * `alg::FirstChernAlgorithms=FHS()`:  The algorithm used to compute the first Chern number. The default is `FHS()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the first Chern number calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: A copy of the input `param_range1`.
      * `param2::AbstractVector`: A copy of the input `param_range2`.
      * `nums::AbstractArray`: An array containing the computed first Chern numbers for each parameter. The size of this array is (**number of bands** × **number of param1** × **number of param2**).

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = Haldane(k, p)
       H(k, p) = H₀(k, (1, p[1], p[2]))
julia> # Set up the first Chern number problem
       prob = FCProblem(H₀)
julia> # Define a parameter range
       param1 = range(-π, π, length=4)
       param2 = range(-6.0, 6.0, length=4)
julia> # Calculate the phase diagram (using the default FHS algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param1, param2; plot=true, progress=true)
(param1 = -3.141592653589793:2.0943951023931953:3.141592653589793, param2 = -6.0:4.0:6.0, nums = [0 0 0 0; 0 0 0 0;;; 0 -1 1 0; 0 1 -1 0;;; 0 -1 1 0; 0 1 -1 0;;; 0 0 0 0; 0 0 0 0])

julia> result.param1
-3.141592653589793:2.0943951023931953:3.141592653589793

julia> result.param2
-6.0:4.0:6.0

julia> result.nums
2×4×4 Array{Int64, 3}:
[:, :, 1] =
 0  0  0  0
 0  0  0  0

[:, :, 2] =
 0  -1   1  0
 0   1  -1  0

[:, :, 3] =
 0  -1   1  0
 0   1  -1  0

[:, :, 4] =
 0  0  0  0
 0  0  0  0
```
