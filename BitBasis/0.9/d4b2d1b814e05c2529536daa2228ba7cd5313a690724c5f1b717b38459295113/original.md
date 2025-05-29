```
SubDitStr{D,N,T<:Integer} <: Integer
```

The struct as a `SubString`-like object for `DitStr`(`SubString` is an official implementation of sliced strings, see [String](https://docs.julialang.org/en/v1/base/strings/#Base.SubString) for reference). This slicing returns a view into the parent `DitStr` instead of making a copy (similar to the `@views` macro for strings).

`SubDitStr` can be used to describe the qubit configuration within the subspace of the entire Hilbert space.It provides similar `getindex`, `length` functions as `DitStr`. 

```
SubDitStr(dit::DitStr{D,N,T}, i::Int, j::Int)
SubDitStr(dit::DitStr{D,N,T}, r::AbstractUnitRange{<:Integer})
```

Or by `@views` macro for `DitStr` (this macro makes your life easier by supporting `begin` and `end` syntax):

```
@views dit[i:j]
```

Returns a `SubDitStr`.

### Examples

```jldoctest
julia> x = DitStr{3, 5}(71)
02122 ₍₃₎

julia> sx =  SubDitStr(x, 2, 4) 
SubDitStr{3, 5, Int64}(02122 ₍₃₎, 1, 3)

julia> @views x[2:end] 
SubDitStr{3, 5, Int64}(02122 ₍₃₎, 1, 4)

julia> sx == dit"212;3"
true
```
