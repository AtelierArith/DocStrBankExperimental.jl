```
function remove(X::Union{Vector, Matrix}, what::Union{Int, Vector{Int}};
				dims=1)
```

Remove one or more elements from a vector or one or more columns or rows from a matrix.

If `X` is a Matrix, `dims`=1 (default) remove rows, `dims`=2 remove columns.

If `X` is a Vector, `dims` has no effect.

The second argument is either an integer or a vector of integers.

**Examples**

```julia
a=randn(5)
b=remove(a, 2)
b=remove(a, collect(1:3)) # remove rows 1 to 3
A=randn(3, 3)
B=remove(A, 2)
B=remove(A, 2; dims=2)
A=randn(5, 5)
B=remove(A, collect(1:2:5)) # remove rows 1, 3 and 5
C=remove(A, [1, 4])
A=randn(10, 10)
A=remove(A, [collect(2:3); collect(8:10)]; dims=2)
```
