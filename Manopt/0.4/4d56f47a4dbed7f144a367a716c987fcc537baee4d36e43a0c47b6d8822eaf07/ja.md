```
update_storage!(a::AbstractStateAction, d::Dict{Symbol,<:Any})
```

[`AbstractStateAction`](@ref) `a`の内部値を辞書`d`に与えられた値に更新します。値はマージされ、`d`からの値が優先されます。
