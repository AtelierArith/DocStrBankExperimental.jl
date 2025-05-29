```
abstract type SHTnsType
```

SHTnsType is an abstract type for the spherical harmonic transform types. All subtypes contain the following keyword arguments:

  * `contiguous_lat::Bool=true`
  * `contiguous_phi::Bool=false`
  * `padding::Bool=false`
  * `gpu::Bool=false`
  * `southpolefirst::Bool=false`
  * `float32::Bool=false`
