make*rectangular(v*arrays::Vector{Vector{T}} where T)

Takes an array of arrays of any type and make it a matrix of `String`.     Arrays can be of different type and length. To make the data rectangular,      it uses the `filler` argument, by default `filler` is an empty string.

## Example 1

```julia
julia> myArrayOfArrays = [["A1","A2", "A3"], ["B1", "B2"], ["C1","C2"]];
julia> make_rectangular(test)
3×3 Matrix{String}:
"A1"  "B1"  "C1"
"A2"  "B2"  "C2"
"A3"  ""    ""
```

## Example 2

```julia
julia> myArrayOfArrays = [["A1","A2", "A3"], [1, 2], ["C1","C2"]];
julia> make_rectangular(test)
3×3 Matrix{String}:
"A1"  "1"  "C1"
"A2"  "2"  "C2"
"A3"  ""    ""
```
