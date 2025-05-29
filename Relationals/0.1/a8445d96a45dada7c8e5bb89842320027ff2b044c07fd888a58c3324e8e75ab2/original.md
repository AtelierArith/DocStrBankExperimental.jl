```
first(T::Type{<:Relational}; kwargs...)
first(T::Type{<:Relational}, cond::Int; kwargs...)
first(T::Type{<:Relational}, cond::String; kwargs...)
first(T::Type{<:Relational}, cond::Pair; kwargs...)
first(T::Type{<:Relational}, cond::UUID; kwargs...)
first(T::Type{<:Relational}, conds::Union{Tuple,AbstractArray}; kwargs...)
```

Gets the first record of type T.

## Examples

```julia
# Gets the first User record.
julia> first(User)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record with id=1.
julia> first(User, 1)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where "uuid IS NOT NULL".
> first(User, "uuid IS NOT NULL")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where last_name="Baggins".
> first(User, :last_name=>"Baggins")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where first_name="Bilbo".
> first(User, :first_name=>:Bilbo)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where uuid="c6dacd6f-0023-4aba-bf24-374f4042fc47".
> first(User, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where id=1 and uuid="c6dacd6f-0023-4aba-bf24-374f4042fc47".
> first(User, (:id=>1, :uuid=>UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47")))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where last_name="Baggins" and uuid is not null.
> first(User, (:last_name=>:Baggins, "uuid IS NOT NULL"))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where last_name="Baggins" and first_name is "Frodo" or "Bilbo". 
> first(User, (:last_name=>:Baggins, :first_name=>["Frodo", "Bilbo"]))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# Gets the first User record where first_name="Frodo" and (id > 1 OR last_name="Baggins").
> first(User, (:first_name=>:Frodo, "id > 1 OR last_name='Baggins'"))
User(2, UUID("0bb0cdc4-b1d3-43ac-93ad-693a94fc9ceb"), "Frodo", "Baggins")
```
