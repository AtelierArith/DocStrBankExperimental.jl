```
UniqueElementsEncoding <: Encoding
UniqueElementsEncoding(x)
```

`UniqueElementsEncoding` is a generic encoding that encodes each `xᵢ ∈ unique(x)` to one of the positive integers. The `xᵢ` are encoded according to the order of their first appearance in the input data.

The constructor requires the input data `x`, since the number of possible symbols is `length(unique(x))`.

## Example

```julia
using ComplexityMeasures
x = ['a', 2, 5, 2, 5, 'a']
e = UniqueElementsEncoding(x)
encode.(Ref(e), x) == [1, 2, 3, 2, 3, 1] # true
```
