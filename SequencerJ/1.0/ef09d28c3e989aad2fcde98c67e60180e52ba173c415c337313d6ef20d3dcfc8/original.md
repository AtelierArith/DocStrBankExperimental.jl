Return the first and last `len` elements of the vector as a string.

Default is to print 3 elements at head and tail.

```julia
julia> v = collect(1:10);
julia> prettyp(v)

"1,2,3...8,9,10"
```

Example w/5 elements visible

```julia
julia> v = collect(1:10);
julia> prettyp(v, 5)

"1,2,3,4,5...6,7,8,9,10"
```
