```
ByRow <: Function
```

`ByRow(f)` returns a function which applies function `f` to each element in a vector.

`ByRow(f)` can be passed two types of arguments:

  * One or more 1-based `AbstractVector`s of equal length: In this case the returned value

is a vector resulting from applying `f` to elements of passed vectors element-wise. Function `f` is called exactly once for each element of passed vectors (as opposed to `map` which assumes for some types of source vectors (e.g. `SparseVector`) that the wrapped function is pure, and may call the function `f` only once for multiple equal values.

  * A `Tables.ColumnTable` holding 1-based columns of equal length: In this case the function

`f` is passed a `NamedTuple` created for each row of passed table.

The return value of `ByRow(f)` is always a vector.

`ByRow` expects that at least one argument is passed to it and in the case of `Tables.ColumnTable` passed that the table has at least one column. In some contexts of operations on tables (for example `DataFrame`) the user might want to pass no arguments (or an empty `Tables.ColumnTable`) to `ByRow`. This case must be separately handled by the code implementing the logic of processing the `ByRow` operation on this specific parent table (the reason is that passing such arguments to `ByRow` does not allow it to determine the number of rows of the source table).

# Examples

```
julia> Tables.ByRow(x -> x^2)(1:3)
3-element Vector{Int64}:
 1
 4
 9

julia> Tables.ByRow((x, y) -> x*y)(1:3, 2:4)
3-element Vector{Int64}:
  2
  6
 12

julia> Tables.ByRow(x -> x.a)((a=1:2, b=3:4))
2-element Vector{Int64}:
 1
 2

 julia> Tables.ByRow(x -> (a=x.a*2, b=sin(x.b), c=x.c))((a=[1, 2, 3],
                                                         b=[1.2, 3.4, 5.6],
                                                         c=["a", "b", "c"]))
3-element Vector{NamedTuple{(:a, :b, :c), Tuple{Int64, Float64, String}}}:
 (a = 2, b = 0.9320390859672263, c = "a")
 (a = 4, b = -0.2555411020268312, c = "b")
 (a = 6, b = -0.6312666378723216, c = "c")

```
