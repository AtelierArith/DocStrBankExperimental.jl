Calculate the one-dimensional phase diagram for the $\mathbb{Z}_2$ number over a specified parameter range.

```
calcPhaseDiagram(prob::Z2Problem, param_range::T1, alg::T2=Shio(); parallel::T3=UseSingleThread(), plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:Z2Algorithms,T3<:TopologicalNumbersParallel}
```

# Description

`calcPhaseDiagram` calculates the $\mathbb{Z}_2$ number for a one-dimensional system described by `Z2Problem` over a range of parameters (`param_range`), constructing a phase diagram. By changing the `alg` or `parallel` options, you can flexibly switch between different calculation methods and parallelization strategies. Moreover, setting `plot=true` generates a simple plot of the results upon completion of the calculation.

# Arguments

  * `prob::Z2Problem`:  A structure that contains the problem settings for $\mathbb{Z}_2$ number calculations, including the Hamiltonian, mesh size, gap information, and other parameters.
  * `param_range::AbstractVector`:  A list or range of parameters (e.g., `range(-2.0, 2.0, length=50)`) over which to scan. The Hamiltonian is evaluated at each parameter value in order to compute the $\mathbb{Z}_2$ number.
  * `alg::Z2Algorithms=Shio()`:  The algorithm used to compute the $\mathbb{Z}_2$ number. The default is `Shio()`. You can implement and specify other algorithms as needed.
  * `parallel::TopologicalNumbersParallel=UseSingleThread()`:  The parallelization strategy. The default is single-threaded (`UseSingleThread()`). If you wish to run in a distributed environment, you can specify it accordingly. (Note that, at present, the $\mathbb{Z}_2$ number calculation does not support multithreading.)
  * `plot::Bool=false`:  If set to `true`, a simple plot of the calculated results is shown after the computation finishes. This is helpful for visually confirming topological phase transitions.
  * `progress::Bool=false`:  If set to `true`, progress is displayed during loop calculations, which can be useful for large-scale computations.

# Returns

  * `NamedTuple{(:param, :nums)}`: 

      * `param::AbstractVector`: A copy of the input `param_range`.
      * `nums::AbstractMatrix`: A matrix containing the computed $\mathbb{Z}_2$ numbers for each parameter. The size of this matrix is (**number of bands** × **number of parameter values**).

# Examples

```julia
julia> using TopologicalNumbers
julia> # Define the Hamiltonian
       H₀(k, p) = BHZ(k, p)
       H(k, p) = H₀(k, (p, 0.25))
julia> # Set up the $\mathbb{Z}_2$ number problem
       prob = Z2Problem(H)
julia> # Define a parameter range
       param = range(-2, 2, length=10)
julia> # Calculate the phase diagram (using the default Shio algorithm, single-threaded,
       # with plotting enabled and progress display)
       result = calcPhaseDiagram(prob, param; plot=true, progress=true)
(param = -2.0:0.4444444444444444:2.0, nums = [0 0; 0 0; 0 0; 1 1; 1 1; 1 1; 1 1; 0 0; 0 0; 0 0])

julia> result.param
-2.0:0.4444444444444444:2.0

julia> result.nums
10×2 Matrix{Int64}:
 0  0
 0  0
 0  0
 1  1
 1  1
 1  1
 1  1
 0  0
 0  0
 0  0
```
