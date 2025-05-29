```
localmap(f, [T=eltype(A),] A, B=3; null=zero(T), order=FORWARD_FILTER)
```

for each position in `A`, applies the function `f` to the values of `A` extracted from the neighborhood defined by `B`.

Optional argument `T` is to specify the element type of the result; by default, `T` is the element type of `A`.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

## Remarks

  * The function `f` is never called with an empty vector of values. Keyword `null` may be used to specify the value of the result where the neighborhood is empty. By default, `null = zero(T)` with `T` the element type of the result.
  * The vector of values passed to `f` may be modified by `f` if needed (for example for faster sorting of the values).

## Examples

With argument `f` set to `minimum` or `maximum`, `localmap` respectively yields the *erosion* and the *dilation* of the input array. However [`erode`](@ref) and [`dilate`](@ref) methods are faster until `localmap` is specialized for these functions.

Applying a *median filter* of the 2-dimensional image `img` in a sliding `5×5` window can be done by:

```julia
using Statistics
med = localmap(median!, img, 5; eltype=float(eltype(img)), null=NaN)
```
