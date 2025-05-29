```
∇imrotate(dy, arr::AbstractArray{T, 4}, θ; method=:bilinear,
                                           rotation_center=size(arr) .÷ 2 .+ 1)
```

Adjoint for `imrotate`. Gradient only with respect to `arr` and not `θ`.

# Arguments

  * `dy`: input gradient
  * `arr`: Input from primal computation
  * `θ`: rotation angle in radians
  * `method=:bilinear` or `method=:nearest`
  * `rotation_center=size(arr) .÷ 2 .+ 1` rotates around a real center pixel for even and odd sized arrays
