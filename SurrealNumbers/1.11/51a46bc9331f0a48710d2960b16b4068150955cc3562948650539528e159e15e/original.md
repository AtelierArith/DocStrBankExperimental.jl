```
generation(x::SurrealFinite)
```

Finds the birthday of a surreal number, which is 1 + the max of any of its components.

## Arguments

  * `x::SurrealFinite`: the number to operate on

## Examples

```jldoctest
julia> generation( convert(SurrealFinite, 1) )
1
```
