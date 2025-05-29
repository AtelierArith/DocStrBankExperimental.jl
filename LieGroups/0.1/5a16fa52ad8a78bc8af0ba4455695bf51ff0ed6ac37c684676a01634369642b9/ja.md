```
cross(O1::AbstractGroupOperation, O2::AbstractGroupOperation)
O1 × O2
O1 × O2 × O3 × ...
```

Return the [`ProductGroupOperation`](@ref) For two [AbstractGroupOperation`](@ref) `O1` and `O2`、一方が[`ProductGroupOperation`](@ref)自体である場合、もう一方は（`O1`が積の場合は前に、`O2`が積の場合は後に）追加されます。両方が積演算である場合、それらは一つに結合され、演算の順序が保持されます。

`×`で二つ以上が連結される場合、これは繰り返されます。
