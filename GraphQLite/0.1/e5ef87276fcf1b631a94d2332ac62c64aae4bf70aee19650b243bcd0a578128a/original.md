```
runmutation(gql::String, vars::Union{<:AbstractDict,Nothing}=nothing, extra::Union{<:AbstractDict,Nothing}=nothing; kwargs...)
```

## Example:

```julia
add_item = "
    mutation AddShoppingCartItem($input: CartItemInput!){
        addItemToCart(input: $input){
            items { $item_fragment }
        }
    }
"
response = runmutation(
    add_item, 
    json2dict("""{"input":{"cartId":1, "itemId":5}}"""),
)
@assert response isa Dict   
@assert response[:addItemToCart] isa Dict
@assert response[:addItemToCart][:items] isa Vector{<:AbstractDict}
```
