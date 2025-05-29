```julia
ishit(buf)

```

Returns true when `buf` index is an integer multiple of datalength of `buf`. 

# Example

```jldoctest
julia> buf = Buffer(3);

julia> for val in 1 : 7
       write!(buf, val)
       @show ishit(buf)
       end
ishit(buf) = false
ishit(buf) = false
ishit(buf) = true
ishit(buf) = false
ishit(buf) = false
ishit(buf) = true
ishit(buf) = false
```
