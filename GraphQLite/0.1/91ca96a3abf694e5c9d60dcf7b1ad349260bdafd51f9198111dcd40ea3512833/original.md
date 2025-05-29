```
runquery(gql::String, vars::Union{<:AbstractDict,Nothing}=nothing, extra::Union{<:AbstractDict,Nothing}=nothing; kwargs...)
```

## Example:

```julia
get_cart = "
    query GetCarts(\$id: Int!){
        myShoppingCart: getCart(id: $id){
            items { id name alternateNames brandId brand{name} }
        }
    }
"
response = runquery(get_cart, json2dict("""{"id":1}"""))
@assert response isa Dict   
@assert response[:myShoppingCart] isa Dict
@assert response[:myShoppingCart][:items] isa Vector{<:AbstractDict}
```
