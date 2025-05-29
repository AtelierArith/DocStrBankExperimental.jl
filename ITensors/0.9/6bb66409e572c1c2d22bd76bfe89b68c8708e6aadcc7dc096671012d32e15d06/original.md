```
ITensor([ElT::Type, ]A::AbstractArray, inds)
ITensor([ElT::Type, ]A::AbstractArray, inds::Index...)

itensor([ElT::Type, ]A::AbstractArray, inds)
itensor([ElT::Type, ]A::AbstractArray, inds::Index...)
```

Construct an ITensor from an AbstractArray `A` and indices `inds`. The ITensor will be a view of the AbstractArray data if possible (if no conversion to a different element type is necessary).

If specified, the ITensor will have element type `ElT`.

If the element type of `A` is `Int` or `Complex{Int}` and the desired element type isn't specified, it will be converted to `Float64` or `Complex{Float64}` automatically. To keep the element type as an integer, specify it explicitly, for example with:

```julia
i = Index(2, "i")
A = [0 1; 1 0]
T = ITensor(eltype(A), A, i', dag(i))
```

# Examples

```julia
i = Index(2,"index_i")
j = Index(2,"index_j")

M = [1. 2;
     3 4]
T = ITensor(M, i, j)
T[i => 1, j => 1] = 3.3
M[1, 1] == 3.3
T[i => 1, j => 1] == 3.3
```

!!! warning
    In future versions this may not automatically convert `Int`/`Complex{Int}` inputs to floating point versions with `float` (once tensor operations using `Int`/`Complex{Int}` are natively as fast as floating point operations), and in that case the particular element type should not be relied on. To avoid extra conversions (and therefore allocations) it is best practice to directly construct with `itensor([0. 1; 1 0], i', dag(i))` if you want a floating point element type. The conversion is done as a performance optimization since often tensors are passed to BLAS/LAPACK and need to be converted to floating point types compatible with those libraries, but future projects in Julia may allow for efficient operations with more general element types (for example see https://github.com/JuliaLinearAlgebra/Octavian.jl).

