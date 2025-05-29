```
Pattern <: AbstractPattern
```

A struct that represents a Julia expression with wildcards. When matching `Pattern`s, it is possilbe for multiple matches to nest within one another.

The fields and constructor of this struct are not part of the public API. See [`@j_str`](@ref) and [`pattern`](@ref) for the public API for creating `Pattern`s.

Methods accepting `Pattern` objects are defined for `eachmatch`, `match`, `findall`, `findfirst`, `findlast`, `occursin`, and `count`.

# Extended Help

The following are implmenetation details:

The expression is stored as an ordinary `SyntaxNode` in the internal `syntax_node` field. Wildcards in that expression are represented by the symbol stored in the internal `wildcard_symbol` field. For example, the expression `a + (b + *)` might be stored as `Pattern((call-i a + (call-i b + wildcard)), :wildcard)`.
