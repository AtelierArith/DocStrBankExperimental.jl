```
get_domain(g::AbstractGrammar, type::Symbol)::BitVector
```

Returns the domain for the hole of a certain type as a `BitVector` of the same length as the number of  rules in the grammar. Bit `i` is set to `true` iff rule `i` is of type `type`.

!!! info
    Since this function can be intensively used when exploring a program space defined by a grammar, the outcomes of this function are precomputed and stored in the `domains` field in a [`AbstractGrammar`](@ref).

