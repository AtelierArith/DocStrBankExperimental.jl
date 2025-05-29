```julia
datalength(buf)

```

Returns the maximum number of data that can be hold in `buf`.

# Example

```jldoctest
julia> buf = Buffer(5);

julia> datalength(buf)
5

julia> buf2 = Buffer(2, 10);

julia> datalength(buf2)
10
```
