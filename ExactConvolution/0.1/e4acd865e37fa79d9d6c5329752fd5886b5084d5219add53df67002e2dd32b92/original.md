```
exact_conv([T,] a, b)
```

Convolve arrays of integers `a` and `b`, and return the resulting array.

$$
exact\_conv(a,b)[k] = \sum_{i+j=k} a[i] \cdot b[j]
$$

# Notes:

  * The implementation uses GMP's BigInt multiplication as the underling DSP engine (FFT for big enough inputs).
  * T must be sufficient to support the result.
  * Using negative values in `a` and `b` is supported but discouraged for runtime reasons.

# Examples

```jldoctest
julia> exact_conv(Int32, [1,2], [4,5,6])
4-element Vector{Int32}:
  4
 13
 16
 12
```
