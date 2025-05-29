```
BubbleSortSwapsEncoding <: Encoding
BubbleSortSwapsEncoding{m}()
```

`BubbleSortSwapsEncoding` is used with [`encode`](@ref) to encode a length-`m` input vector `x` into an integer in the range `ω ∈ 0:((m*(m-1)) ÷ 2)`, by counting the number  of swaps required for the bubble sort algorithm to sort `x` in ascending order. 

[`decode`](@ref) is not implemented for this encoding.

## Example

```julia
using ComplexityMeasures
x = [1, 5, 3, 1, 2]
e = BubbleSortSwapsEncoding{5}() # constructor type argument must match length of vector 
encode(e, x)
```
