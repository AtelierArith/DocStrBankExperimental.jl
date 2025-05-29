```
canonicalise(s::SurrealFinite)
```

Convert a surreal number form into its equivalent canonical form. It performs the   conversion by converting to a Rational and then back to a Surreal.  

## Examples

```jldoctest
julia> convert(SurrealFinite, 1) - convert(SurrealFinite, 1)
{ { ϕ | { ϕ | ϕ } } | { { ϕ | ϕ } | ϕ } }
julia> pf( canonicalise( convert(SurrealFinite, 1) - convert(SurrealFinite, 1) ) )
{ ϕ | ϕ }
```
