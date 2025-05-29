```
@SLVector Names
@SLVector Eltype Names
```

The macro creates a labelled static vector with element type `ElType`, and names from `Names`. If no eltype is given, then the eltype is determined from the values in the constructor. The array size is found from the input data.

For example:

```julia
ABC = @SLVector (:a, :b, :c)
x = ABC(1.0, 2.5, 3.0)
x.a == 1.0
x.b == 2.5
x.c == x[3]
```
