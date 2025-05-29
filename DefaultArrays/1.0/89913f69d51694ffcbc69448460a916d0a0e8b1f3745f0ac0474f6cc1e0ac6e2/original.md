eachnondefault(A::DefaultArray, indexstyle = IndexLinear())

Create an generator object for visiting each index of a `DefaultArray A` containing a non-default value, in an efficient manner.

Example:

```julia
julia> A = DefaultArray(1,[1 2; 3 4]);

julia> for i in eachnondefault(A) # linear indexing
           println(i, " ", A[i])
       end
4 4
2 3
3 2
```

notice how the value "1" has been skipped, since we set 1 as the default value.

```julia
julia> A = DefaultArray(1,[1 2; 3 4]);

julia> for i in eachnondefault(A,IndexCartesian()) # cartesian indexing
           println(i, " ", A[i])
       end
CartesianIndex(2, 2) 4
CartesianIndex(2, 1) 3
CartesianIndex(1, 2) 2
```
