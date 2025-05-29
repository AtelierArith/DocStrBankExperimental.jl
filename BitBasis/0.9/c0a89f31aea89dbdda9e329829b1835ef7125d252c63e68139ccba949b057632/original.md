```
DitStr{D,N,T<:Integer} <: Integer
```

The struct for dit string with fixed length `N` and storage type `T`, where `dit` is a extension of `dit` from binary system to a d-ary system.

```
DitStr{D,N,T}(integer)
DitStr{D,N}(integer)
DitStr{D}(vector)
```

Returns a `DitStr`. When the input is an integer, the dits are read from right to left. When the input is a vector, the dits are read from left to right.

### Examples

```jldoctest
julia> DitStr{3}([1,2,1,1,0])
01121 ₍₃₎

julia> DitStr{3, 5}(71)
02122 ₍₃₎
```
