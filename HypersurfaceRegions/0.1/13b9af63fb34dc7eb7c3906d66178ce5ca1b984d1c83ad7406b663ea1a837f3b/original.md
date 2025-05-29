```
regions(f::Vector{Expression})
regions(f::System)
```

Input a list of hypersurfaces 'f = [f*1,...f*k]'. Outputs the regions in the complement of the hypersurface arrangement, their sign patterns, Euler characteristic and the indices of the critical points in each region.

Options:

  * `bounded_check = false`: if true, the algorithm also computes if regions are bounded or unbounded.
  * `projective_fusion = false`: if `true`, the algorithm computes which of the regions are fused at infinity.
  * `target_parameters`: Specify parameters of the [System](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/systems/) `f` (if its has any).
  * `show_progress = true`: if true, prints the progress of the computation to the terminal.
  * `s`: exponents of the Morse function `f_1^(s_1) * ... * f_k^(s_k) * q^(s_k+1)`. Here, `s` is a list of integers `[s_1, ..., s_k, s_{k+1}]` such that `s_1, ..., s_k>0, s_{k+1}<0` and `2 s_{k+1} > s_1 deg(f_1) + ... + s_k deg(f_k)`.
  * `epsilon = 1e-6`: how close from each critical point do we do the path tracking.
  * `reltol = 1e-6`, `abstol = 1e-9`: parameters for the accuracy of the ODE solver.
  * `monodromy_options = MonodromyOptions(max_loops_no_progress = 25)`: pass options for [monodromy](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/monodromy/).
  * `start_pair_using_newton::Bool = false`: if true, the algorithm tries to compute a start pair for monodromy by using Newton's methods. Can reduce the number of critical points, but is less stable.

Options for when `bounded_check = true`:

  * `δ::Float64 = 1e-8`: Parameter that defines the strip around infinity.

## Example

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
regions(f)
```

## Example with information on boundedness

```julia
regions(f; bounded_check = true)
```
