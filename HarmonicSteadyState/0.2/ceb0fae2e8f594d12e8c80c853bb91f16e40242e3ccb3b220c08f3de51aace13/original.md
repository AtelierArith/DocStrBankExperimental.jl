```
get_steady_states(
    prob::HomotopyContinuationProblem,
    method::HomotopyContinuationMethod;
    show_progress=true,
    sorting="nearest",
    classify_default=true,
    verbose=false
    )
```

Solves `problem` with the `method` over the ranges specified by `swept_parameters`, keeping `fixed_parameters` constant. `swept_parameters` accepts pairs mapping symbolic variables to arrays or ranges. `fixed_parameters` accepts pairs mapping symbolic variables to numbers.

### Keyword arguments

  * `show_progress`: Indicate whether a progress bar should be displayed.
  * `sorting`: the method used by `sort_solutions` to get continuous solutions branches.   The current options are `"hilbert"` (1D sorting along a Hilbert curve), `"nearest"`   (nearest-neighbor sorting) and `"none"`.
  * `classify_default`: If `true`, the solutions will be classified using the default   classification method.

### Example

solving a simple harmonic oscillator $m \ddot{x} + γ \dot{x} + ω_0^2 x = F \cos(ωt)$ to obtain the response as a function of $ω$

```julia-repl
# having obtained a HomotopyContinuationProblem object, let's find steady states
julia> range = (ω => range(0.8, 1.2, 100) ) # 100 parameter sets to solve
julia> fixed = ParameterList(m => 1, γ => 0.01, F => 0.5, ω_0 => 1)
julia> get_steady_states(problem, range, fixed)

A steady state result for 100 parameter points

    Solution branches:   1
       of which real:    1
       of which stable:  1

    Classes: stable, physical, Hopf, binary_labels

```

It is also possible to perform 2-dimensional sweeps.

```julia-repl
# The swept parameters take precedence over fixed -> use the same fixed
julia> range = (ω => range(0.8,1.2,100), F => range(0.1,1.0,10) )

# The swept parameters take precedence over fixed -> the F in fixed is now ignored
julia> get_steady_states(problem, range, fixed)

A steady state result for 1000 parameter points

    Solution branches:   1
       of which real:    1
       of which stable:  1

    Classes: stable, physical, Hopf, binary_labels
```
