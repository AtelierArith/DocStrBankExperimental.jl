`joindigits(l::AbstractVector{Int},delim="()";sep=",")`

print  a list `l` of  (usually small) numbers as  compactly as possible: no separators if all numbers are smaller than 10.

```julia-repl
julia> joindigits([1,9,3,5])
"1935"

julia> joindigits([1,10,3,5])
"(1,10,3,5)"

julia> joindigits([1,10,3,5],"[]";sep="-")
"[1-10-3-5]"
```
