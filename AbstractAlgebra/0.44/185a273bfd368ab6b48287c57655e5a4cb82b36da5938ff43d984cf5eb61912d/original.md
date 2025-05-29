```
zero(x::MatElem{T}, R::NCRing, r::Int, c::Int) where T <: NCRingElement
zero(x::MatElem{T}, r::Int, c::Int) where T <: NCRingElement
zero(x::MatElem{T}, R::NCRing) where T <: NCRingElement
zero(x::MatElem{T}) where T <: NCRingElement
```

Create an zero matrix over the given ring and dimensions, with defaults based upon the given source matrix `x`.
