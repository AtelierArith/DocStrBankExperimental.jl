```julia
connect!(outpin, inpin)

```

Connects `outpin` to `inpin`. When connected, any element that is put into `outpin` is also put into `inpin`. 

# Example

```jldoctest
julia> op, ip = Outpin(), Inpin();

julia> l = connect!(op, ip)
Link(state:open, eltype:Float64, isreadable:false, iswritable:false)

julia> l in op.links
true

julia> ip.link === l
true
```
