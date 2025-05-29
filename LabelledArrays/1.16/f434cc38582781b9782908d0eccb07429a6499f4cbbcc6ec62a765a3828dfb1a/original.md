```julia
SLVector(::NamedTuple)
SLVector(kwargs)
```

The standard constructors for `SLArray`.

```julia
julia> SLVector(a = 1, b = 2, c = 3)
3-element SLArray{Tuple{3},1,(:a, :b, :c),Int64}:
 1
 2
 3
```

Constructing copies with some items changed is supported by a keyword constructor whose first argument is the source and whose additional keyword arguments indicate the changes.

```julia
julia> v1 = SLVector(a = 1.1, b = 2.2, c = 3.3);

julia> v2 = SLVector(v1; b = 20.20, c = 30.30)
3-element SLArray{Tuple{3},Float64,1,3,(:a, :b, :c)}:
  1.1
 20.2
 30.3
```

Additional examples:

```julia
SLVector((a = 1, b = 2))
SLVector(a = 1, b = 2)
```
