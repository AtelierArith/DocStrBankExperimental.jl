```julia
mutable struct Link{T}
```

A `Link` connects an Outpin and Inpin for data flow. See [`Outpin`](@ref), [`Inpin`](@ref), [`connect!`](@ref)

# Fields

  * `buffer::Causal.Buffer{Causal.Cyclic, T, 1} where T`: Internal buffer to record data flowing throgh link
  * `channel::Channel`: Internal channel for data flow
  * `masterid::Base.UUID`: Unique identifier of the outpin of the source of the link
  * `slaveid::Base.UUID`: Unique identifier fo the inpin of the destination of the link
  * `id::Base.UUID`: Unique identifier

# Example

```jldoctest
julia> l = Link{Int}(5)
Link(state:open, eltype:Int64, isreadable:false, iswritable:false)

julia> l = Link{Bool}()
Link(state:open, eltype:Bool, isreadable:false, iswritable:false)
```
