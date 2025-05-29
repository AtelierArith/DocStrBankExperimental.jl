```
@SLArray Size Names
@SLArray Eltype Size Names
```

The macro creates a labelled static vector with element type `ElType`, names from `Names`, and size from `Size`. If no eltype is given, then the eltype is determined from the arguments in the constructor.

For example:

```julia
ABCD = @SLArray (2, 2) (:a, :b, :c, :d)
x = ABCD(1.0, 2.5, 3.0, 5.0)
x.a == 1.0
x.b == 2.5
x.c == x[3]
x.d == x[2, 2]
EFG = @SLArray (2, 2) (e = 1:3, f = 4, g = 2:4)
y = EFG(1.0, 2.5, 3.0, 5.0)
EFG = @SLArray (2, 2) (e = (2, :), f = 4, g = 2:4)
```

Users can also specify the indices directly.

```julia
julia> EFG = @SLArray (2, 2) (e = 1:3, f = 4, g = 2:4);

julia> y = EFG(1.0, 2.5, 3.0, 5.0)
2×2 SLArray{Tuple{2,2},Float64,2,4,(e = 1:3, f = 4, g = 2:4)}:
 1.0  3.0
 2.5  5.0

julia> y.g
3-element view(reshape(::StaticArrays.SArray{Tuple{2,2},Float64,2,4}, 4), 2:4) with eltype Float64:
 2.5
 3.0
 5.0

julia> Arr = @SLArray (2, 2) (a = (2, :), b = 3);

julia> z = Arr(1, 2, 3, 4);

julia> z.a
2-element view(::StaticArrays.SArray{Tuple{2,2},Int64,2,4}, 2, :) with eltype Int64:
 2
 4
```
