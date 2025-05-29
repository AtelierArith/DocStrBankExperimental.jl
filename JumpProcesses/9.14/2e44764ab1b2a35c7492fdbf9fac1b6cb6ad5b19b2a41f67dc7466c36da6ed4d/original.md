```julia
struct RegularJump{iip, R, C, MD}
```

Representation for encoding rates and multiple simultaneous jumps for use in τ-leaping type methods.

### Constructors

  * `RegularJump(rate, c, numjumps; mark_dist = nothing)`

## Fields

  * `rate`: Function `rate!(rate_vals, u, p, t)` that returns the current rates, i.e. intensities or propensities, for all possible jumps in `rate_vals`.

  * `c`: Function `c(du, u, p, t, counts, mark)` that executes the `i`th jump `counts[i]` times, saving the output in `du[i]`.

  * `numjumps`:  Number of jumps in the system.
  * `mark_dist`:  A distribution for marks. Not currently used or supported.

## Examples

```julia
function rate!(out, u, p, t)
    out[1] = (0.1 / 1000.0) * u[1] * u[2]
    out[2] = 0.01u[2]
    nothing
end

const dc = zeros(3,2)
function c(du, u, p, t, counts, mark) 
    mul!(du, dc, counts)
    nothing
end

rj = RegularJump(rate!, c, 2)

## Notes
- `mark_dist` is not currently used or supported in τ-leaping methods.
```
