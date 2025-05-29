```
@belongs_to(model_type::QuoteNode, attr_name::Expr)
```

Generates a function named "get{attr_name}" to retrieve a single object that is mapped to the model object. 

## Examples

```julia
# Configure a "getaddress" function for a User object.
@belongs_to User :address

# Configure a "getadmin" function for a Manufacturer object.
@belongs_to Manufacturer :admin=>User
```

```julia
# Gets the address of a user.
julia> getaddress(first(User))
Address(1, "1 Bagshot Row", "Shire", "Middle Earth", "37012")

# Gets the location of a manufacturer.
julia> getadmin(first(Manufacturer, 1))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")
```
