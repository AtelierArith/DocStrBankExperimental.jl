`retag(replacements::Dict{ScopeTag, ScopeTag}, x::T) where {T} -> T`

Recurse through the structure of `x`, swapping any instance of a ScopeTag `t` with `get(replacements, t, t)`. Overload this function on structs that have ScopeTags within them.
