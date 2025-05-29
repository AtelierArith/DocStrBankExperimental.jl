```
∇grid_sample(Δ::AbstractArray{T, 4}, input::AbstractArray{T, 4}, grid::AbstractArray{T, 4}; padding_mode = :zeros) where T
```

# Arguments

  * `Δ`: Input gradient in `(W_out, H_out, C, N)` shape   (same as output of the primal computation).
  * `input`: Input from primal computation in `(W_in, H_in, C, N)` shape.
  * `grid`: Grid from primal computation in `(2, W_out, H_out, N)` shape.
  * `padding_mode`: Out-of-bound padding.   `:zeros` to use `0` for out-of-bound grid locations.   `:border` to use border values for out-of-bound grid locations.   Should be the same as in primal computation.   Default is `:zeros`.

# Returns

`dinput` (same shape as `input`) and `dgrid` (same shape as `grid`) gradients.
