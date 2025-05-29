```
resolveinput(field::Val{F}, d::T)
```

## Example:

```julia

@schema """
...
type Mutation {
    addItemToCart(input: CartItemInput): Cart
}
...
input CartItemInput {
    cartId: Int!
    itemId: Int!
    quantity: Int!
}
...
"""

@kwdef struct CartItemInput
    quantity::Int = 1
    cart_id::Int
    item_id::Int
end

GraphQLite.resolveinput(::Val{:CartItemInput}, d::Dict) = CartItemInput(d)
```
