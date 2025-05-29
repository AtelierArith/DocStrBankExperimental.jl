```
meanpool(x, k::NTuple{N, Integer}; pad=0, stride=k)
```

Perform mean pool operation with window size `k` on input tensor `x`.

Arguments:

  * `x` and `k`: Expects `ndim(x) ∈ 3:5`, and always `length(k) == ndim(x) - 2`
  * `pad`: See [`pad_zeros`](@ref) for details.
  * `stride`: Either a tuple with the same length as `k`, or one integer for all directions. Default is `k`.
