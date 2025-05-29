```
ChebyshevTransform(; modes)
```

Constructs a discrete Chebyshev transform transform with modes `modes` that  operates on the 2nd, 3rd, ...N-modes+1-st dimension of the data. Input must be have even-numbered size.

# Example

```
julia> ChebyshevTransform(modes = (12, 3, 4, 12))
```
