```
dict2struct(::Type{T}, d::Dict)
```

## Convenience method for converting a Dict to a custom type.

## Example:

```julia

@kwdef struct CartItemInput
    quantity::Int = 1
    cart_id::Int
    item_id::Int
end

@assert dict2struct(CartItemInput, Dict(:cart_id=>1, :item_id=>2)) == CartItemInput(1, 1, 2)
```
