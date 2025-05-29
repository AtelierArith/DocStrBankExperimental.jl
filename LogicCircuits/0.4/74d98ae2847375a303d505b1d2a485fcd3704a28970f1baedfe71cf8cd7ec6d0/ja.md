```
forget(α::Bdd, x::Integer)::Bdd = eliminate(α, x)
forget(α::Bdd, X::Union{Set, BitSet, AbstractVector{T}}) where T <: Integer
```

`forget`操作を適用した後の結果のBDDを返します。$\phi|_x \vee \phi|_{\neg x}$に相当します。
