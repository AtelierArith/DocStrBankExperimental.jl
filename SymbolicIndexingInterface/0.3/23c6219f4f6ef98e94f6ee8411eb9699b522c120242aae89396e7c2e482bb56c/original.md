```
struct BatchedInterface{S <: AbstractVector, I}
function BatchedInterface(indp_syms::Tuple...)
```

A struct which stores information for batched calls to [`getsym`](@ref) or [`setsym`](@ref). Given `Tuple`s, where the first element of each tuple is an index provider and the second an array of symbolic variables (either states or parameters) in the index provider, `BatchedInterface` will compute the union of all symbols and associate each symbol with the first index provider with which it occurs.

For example, given two index providers `s1 = SymbolCache([:x, :y, :z])` and `s2 = SymbolCache([:y, :z, :w])`, `BatchedInterface((s1, [:x, :y]), (s2, [:y, :z]))` will associate `:x` and `:y` with `s1` and `:z` with `s2`. The information that `s1` had associated symbols `:x` and `:y` and `s2` had associated symbols `:y` and `:z` will also be retained internally.

`BatchedInterface` implements [`variable_symbols`](@ref), [`is_variable`](@ref), [`variable_index`](@ref) to query the order of symbols in the union.

See [`getsym`](@ref) and [`setsym`](@ref) for further details.

See also: [`associated_systems`](@ref).
