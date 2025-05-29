```
expand(x::SurrealFinite; level=0)
```

Writes a surreal as a string with varying levels of expansion.

## Arguments

  * `x::SurrealFinite`: the number of elements to expand
  * `level=0`: the amount of expansion

      * 0 : write shorthand if it exists, or $\{ X_L \| X_R \}$ if not
      * 1 : $\{ X_L \| X_R \}$
      * 2 : expand out $X_L$ and $X_R$ recursively

## Examples

```jldoctest
julia> expand( convert(SurrealFinite, 2))
"2"
julia> expand( convert(SurrealFinite, 2); level=1)
"{ 1 | ∅ }"
julia> expand( convert(SurrealFinite, 2); level=2)
"{ { { ∅ | ∅ } | ∅ } | ∅ }"
```
