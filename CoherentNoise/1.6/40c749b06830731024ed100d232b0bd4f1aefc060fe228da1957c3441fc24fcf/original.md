```
warp(source::AbstractSampler; kwargs...)
```

Construct a modifier sampler that performs domain warping of the sampler `source` before sampling from it.

Domain warping feeds the output of other samplers to the input of a sampler. For this modifier, each input coordinate can specify a different sampler to warp with.

If a sampler is not supplied for `x`, `y`, `z`, or `w`, a sampler that outputs a constant zero will be used instead.

# Arguments

  * `x::AbstractSampler=constant_1d()`: A sampler to warp the X axis by.
  * `y::AbstractSampler=constant_1d()`: A sampler to warp the Y axis by.
  * `z::AbstractSampler=constant_1d()`: A sampler to warp the Z axis by.
  * `w::AbstractSampler=constant_1d()`: A sampler to warp the W axis by.
