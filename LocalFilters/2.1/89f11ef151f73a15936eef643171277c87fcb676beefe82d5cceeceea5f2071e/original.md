```
localreduce(op, [T=eltype(A),] A, dims, rngs; kwds...) -> dst
```

yields the local reduction by the associative binary operator `op` of the values of `A` into contiguous hyper-rectangular neighborhoods defined by the interval(s) `rngs` along dimension(s) `dims` of `A`. The algorithm of van Herk-Gil-Werman is used to compute the reduction.

Optional argument `T` is to specify the element type of the result.

Argument `dims` specifies along which dimension(s) of `A` the local reduction is to be applied, it can be a single integer, a tuple of integers, or a colon `:` to apply the operation to all dimensions. Dimensions are processed in the order given by `dims` (the same dimension may appear several times) and there must be a matching interval in `rngs` to specify the structuring element (except that, if `rngs` is a single interval, it is used for every dimension in `dims`). An interval is either an integer or an integer valued unit range in the form `kmin:kmax`. An interval specified as a single integer is treated as an approximately centered range of this length.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

Keyword `work` may be used to provide a workspace array of type `Vector{T}` which is automatically resized as needed.

Assuming a mono-dimensional array `A`, the single reduction pass:

```
dst = localreduce(op, A, :, rng)
```

amounts to computing (assuming forward ordering):

```
dst[j] =  A[i+kmin] ⋄ A[i+kmin+1] ⋄ ... ⋄ A[i+kmax-1] ⋄ A[i+kmax]
```

for all `j ∈ axes(dst,1)`, with `x ⋄ y = op(x, y)`, `kmin = first(rng)` and `kmax = last(rng)`. Note that if `kmin = kmax = k`, the result of the filter is to operate a simple shift by `k` along the corresponding dimension and has no effects if `k = 0`. This can be exploited to not filter some dimension(s).

Flat boundary conditions are assumed for `A[i+k]` in the above formula.

## Examples

The *morphological erosion* (local minimum) of the array `A` on a centered structuring element of width 7 in every dimension can be obtained by:

```
localreduce(min, A, :, -3:3)
```

or equivalently by:

```
localreduce(min, A, :, 7)
```

Index interval `0:0` may be specified to do nothing along the corresponding dimension. For instance, assuming `A` is a three-dimensional array:

```
localreduce(max, A, :, (-3:3, 0:0, -4:4))
```

yields the *morphological dilation* (*i.e.* local maximum) of `A` in a centered local neighborhood of size `7×1×9` (nothing is done along the second dimension). The same result may be obtained with:

```
localreduce(max, A, (1,3), (-3:3, -4:4))
```

where the second dimension is omitted from the list of dimensions.

The *local average* of the two-dimensional array `A` on a centered sliding window of size 11×11 can be computed as:

```
localreduce(+, A, :, (-5:5, -5:5)) ./ 11^2
```

See [`localreduce!`](@ref) for an in-place version of the method.
