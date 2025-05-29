```
create_bias(weights, bias, size...)
```

Return a bias parameter for a layer, based on the value given to the constructor's keyword `bias=bias`.

  * `bias == true` creates a trainable array of the given size, of the same type as `weights`, initialised to zero.
  * `bias == false` returns `false`, which is understood by AD to be non-differentiable.
  * `bias::AbstractArray` uses the array provided, provided it has the correct size. It will also correct the `eltype` to match that of `weights`.
