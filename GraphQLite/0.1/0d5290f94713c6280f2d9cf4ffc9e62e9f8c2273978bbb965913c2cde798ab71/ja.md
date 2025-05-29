```
dict2struct(::Type{T}, d::Dict)
```

## Dictをカスタムタイプに変換するための便利なメソッド。

## 例:

```julia

@kwdef struct CartItemInput
    quantity::Int = 1
    cart_id::Int
    item_id::Int
end

@assert dict2struct(CartItemInput, Dict(:cart_id=>1, :item_id=>2)) == CartItemInput(1, 1, 2)
```
