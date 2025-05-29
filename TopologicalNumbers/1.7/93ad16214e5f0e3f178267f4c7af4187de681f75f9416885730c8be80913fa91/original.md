Calculate the two-dimensional phase diagram for the second Chern number over a specified parameter range.

```
calcPhaseDiagram(prob::SCProblem, param_range1::T1, param_range2::T2, alg::T3=FHS2(); parallel::T4=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:SecondChernAlgorithms,T4<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the second Chern number for a two-dimensional system described by `SCProblem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::SCProblem`:  A structure that contains the problem settings for second Chern number calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range1::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the second Chern number.
  * `param_range2::AbstractVector`: A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the second Chern number.
  * `alg::SecondChernAlgorithms=FHS2()`:  The algorithm used to compute the second Chern number. The default is `FHS2()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the second Chern number calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param1::AbstractVector`: A copy of the input `param_range1`.
      * `param2::AbstractVector`: A copy of the input `param_range2`.
      * `nums::AbstractArray`: An array containing the computed second Chern numbers for each parameter. The size of this array is (**number of bands** × **number of param1** × **number of param2**).
