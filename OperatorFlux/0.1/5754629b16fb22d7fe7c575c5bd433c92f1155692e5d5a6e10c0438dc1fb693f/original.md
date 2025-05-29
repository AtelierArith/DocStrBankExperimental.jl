```
FourierTransform(; modes, even = true)
```

Constructs a discrete Fourier transform with modes `modes` and style `even` that  operates on the 2nd, 3rd, ...N-modes+1-st dimension of the data.

# Example

```
julia> FourierTransform(modes = (12, 3, 4, 12))
```
