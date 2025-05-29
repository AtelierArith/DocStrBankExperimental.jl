`rename(tag::ScopeTag, replacements::Dict{Symbol, Symbol}, x::T) where {T} -> T`

Recurse through the structure of `x`, and change any name `n` in scope `tag` to `get(replacements, n, n)`. Overload this function on structs that have names in them.
