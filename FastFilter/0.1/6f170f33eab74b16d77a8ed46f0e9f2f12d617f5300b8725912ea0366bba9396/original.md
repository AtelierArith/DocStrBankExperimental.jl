`BinaryFuseFilter{T}( 	keys::Vector{UInt64};  	seed = UInt64(0x726b2b9d438b9d4d),  	max_iterations = 10) where T <: Union{UInt8, UInt16, UInt32}`

Build a binary fuse filter with T type fingerprints from keys in `keys`. 

## Arguments

`seed` is used as initial seed value,  which is iteratively changed during structure build step. 

`max_iterations` restricts how many rounds of build step to try  before termination.

# Examples

```julia-repl
julia> filter = BinaryFuseFilter{UInt8}(UInt64.[1:10])
BinaryFuseFilter with 10 keys and seed 1198702242888554850.

julia> UInt64(1) in filter
true

julia> UInt64(11) in filter
false
```
