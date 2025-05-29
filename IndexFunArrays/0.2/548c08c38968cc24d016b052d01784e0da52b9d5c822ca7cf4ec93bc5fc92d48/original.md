```
IndexFunArray([T], gen::F, size::NTuple{N,Int}) where {N,F}
```

Generate a IndexFunArray object which behaves like an array but does not allocate the full array. Instead it calculates the elements when needed. This is useful to prevent array allocations. `gen` is a function which takes the array indices wrapped as tuple as input. The output of `gen` determines the element type of the resulting array. `size` is the output size of the resulting array. `T` can be the optional element type of the arrays.  `gen` needs to have `T` as return type, otherwise the IndexFunArray might be type unstable.

# Examples

```julia-repl
julia> IndexFunArray(x -> sum(x), (3, 3))
3×3 IndexFunArray{Int64, 2, var"#182#183"}:
 2  3  4
 3  4  5
 4  5  6

julia> IndexFunArray(x -> sum(abs2.(x)), (3, 3))
3×3 IndexFunArray{Int64, 2, var"#184#185"}:
  2   5  10
  5   8  13
 10  13  18

julia> IndexFunArray(x -> (x[1], x[2], "Julia"), (3,3))
3×3 IndexFunArray{Tuple{Int64, Int64, String}, 2, var"#18#19"}:
 (1, 1, "Julia")  (1, 2, "Julia")  (1, 3, "Julia")
 (2, 1, "Julia")  (2, 2, "Julia")  (2, 3, "Julia")
 (3, 1, "Julia")  (3, 2, "Julia")  (3, 3, "Julia")
```
