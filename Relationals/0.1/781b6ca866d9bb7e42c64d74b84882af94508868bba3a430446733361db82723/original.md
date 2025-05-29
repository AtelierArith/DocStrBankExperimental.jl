```
all(T::Type{<:Relational}; kwargs...)
all(T::Type{<:Relational}, cond::String; kwargs...)
all(T::Type{<:Relational}, cond::Pair; kwargs...)
all(T::Type{<:Relational}, conds::Union{Tuple,AbstractArray}; kwargs...)
```

Gets a collection of records of type T.

## Examples

```julia
julia> all(User)
3-element Vector{User}:
 User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins", 1)
 User(2, UUID("32002bdb-0435-42e4-9c7b-e7dea3162abb"), "Frodo", "Baggins", 1)
 User(3, UUID("fe6fe463-10c0-4bbc-bb39-bbd6f55a9e06"), "Samwise", "Gamgee", 2)

julia> all(User, "uuid IS NOT NULL")
3-element Vector{User}:
 User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins", 1)
 User(2, UUID("32002bdb-0435-42e4-9c7b-e7dea3162abb"), "Frodo", "Baggins", 1)
 User(3, UUID("fe6fe463-10c0-4bbc-bb39-bbd6f55a9e06"), "Samwise", "Gamgee", 2)

julia> all(User, :last_name=>"Baggins")
2-element Vector{User}:
 User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins", 1)
 User(2, UUID("32002bdb-0435-42e4-9c7b-e7dea3162abb"), "Frodo", "Baggins", 1)

julia> all(User, ("uuid IS NOT NULL", :last_name=>"Baggins"); limit=2)
2-element Vector{User}:
 User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins", 1)
 User(2, UUID("32002bdb-0435-42e4-9c7b-e7dea3162abb"), "Frodo", "Baggins", 1)

```
