```
cv = conv(u::AbstractArray{<:Number, N}, v::AbstractArray{<:Number, N}; shape=:full)
```

Convolution of two arrays.

If `u,v` are vectors returns the convolution of vectors u and v. If `u,v` are matrices returns the two-dimensional convolution of matrices A and B.

The keyword argument `shape` controls if we return the full convolution result (the default) or only the central part of the convolution, the same size as `u`. In the first case (for the 1D case), the length of the output is `length(u) + length(v) - 1`.

When we are using convolution to do filtering, we are normaly interested in recieving a result that is of the same size of `u`. In this case, use the option `shape=:same` (in fact, anything different from `:full` will work). But if we were multiplying polynomes, then we would want all convolution terms and `shape=:full` (again, the default) would give us that.

### Example

```julia
julia> conv([-1, 2, 3, -2, 0, 1, 2], [2, 4, -1, 1], shape=:same)
7-element Vector{Int64}:
 15
  5
 -9
  7
  6
  7
 -1
```
