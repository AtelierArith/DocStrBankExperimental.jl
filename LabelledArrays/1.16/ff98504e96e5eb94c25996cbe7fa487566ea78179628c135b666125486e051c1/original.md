```julia
SLArray{::Tuple}(::NamedTuple)
SLArray{::Tuple}(kwargs)
```

These are the standard constructors for `SLArray`. For general N-dimensional labelled arrays, users need to specify the size (`Tuple{dim1,dim2,...}`) in the type parameter to the `SLArray` constructor:

```julia
julia> SLArray{Tuple{2, 2}}((a = 1, b = 2, c = 3, d = 4))
2×2 SLArray{Tuple{2, 2}, Int64, 2, 4, (:a, :b, :c, :d)} with indices SOneTo(2)×SOneTo(2):
 :a => 1  :c => 3
 :b => 2  :d => 4

julia> SLArray{Tuple{2, 2}}(a = 1, b = 2, c = 3, d = 4)
 2×2 SLArray{Tuple{2,2},2,(:a, :b, :c, :d),Int64}:
 1  3
 2  4
```

Constructing copies with some changed elements is supported by a keyword constructor whose first argument is the source and whose additional keyword arguments indicate the changes.

```julia
julia> ABCD = @SLArray (2, 2) (:a, :b, :c, :d);

julia> B = ABCD(1, 2, 3, 4);

julia> B2 = SLArray(B; c = 30)
2×2 SLArray{Tuple{2,2},Int64,2,4,(:a, :b, :c, :d)}:
 1  30
 2   4
```

Additional examples:

```julia
SLArray{Tuple{2, 2}}((a = 1, b = 2, c = 3, d = 4))
```
