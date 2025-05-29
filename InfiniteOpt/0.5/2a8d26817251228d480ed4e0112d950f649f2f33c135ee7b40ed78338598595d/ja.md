```
domain_restrictions(cref::InfOptConstraintRef)::DomainRestrictions{GeneralVariableRef}
```

制約 `cref` に関連付けられた [`DomainRestrictions`](@ref) オブジェクトを返します。

**例**

```julia-repl
julia> domain_restrictions(cref)
サブドメイン制約 (1): t ∈ [0, 2]
```
