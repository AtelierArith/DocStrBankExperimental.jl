```
ValInserter(Components::AbstractVector{<:Int}, Values::AbstractVector{<:AbstractFloat}) -> Function
```

Returns an embedding function which inserts `Values` in the specified `Components`. In effect, this allows one to pin multiple input components at a specific values.
