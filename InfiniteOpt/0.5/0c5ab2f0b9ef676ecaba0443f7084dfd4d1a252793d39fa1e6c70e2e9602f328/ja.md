```
has_domain_restrictions(cref::InfOptConstraintRef)::Bool
```

`cref`が[`DomainRestrictions`](@ref)オブジェクトによって定義されたサブドメインに制限されているかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> has_domain_restrictions(cref)
true
```
