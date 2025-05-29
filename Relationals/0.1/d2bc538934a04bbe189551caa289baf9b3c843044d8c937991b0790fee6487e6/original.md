```
update(T::Type{<:Relational}, key::Union{Int,UUID}, value::Pair; kwargs...)
update(T::Type{<:Relational}, key::Union{Int,UUID}, values::Union{Tuple,AbstractArray}; kwargs...)
```

Updates the record matching the unique key (either :id of type Int or :uuid of type UUID) with value(s)

## Examples

```julia
# Gets the first User record.
julia> update(Manufacturer, 1, :name=>"Sauron Supplies")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record.
julia> update(Manufacturer, 1, (:name=>"Sauron Supplies", :admin_id=>1))
User(1, update("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")
```
