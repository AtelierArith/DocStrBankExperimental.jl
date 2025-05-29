```
struct ExplicitAlphabet{V} <: AbstractAlphabet{V}
    atoms::Vector{Atom{V}}
end
```

原子を（有限の）`Vector`でラップするアルファベットです。

詳細は[`AbstractAlphabet`](@ref)、[`atoms`](@ref)を参照してください。
