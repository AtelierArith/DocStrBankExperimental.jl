```
combination_pairs(T::Type{<:BitMask})
```

Return a vector of `name => combination::T` pairs for all values of type `T` that that do not define a new flag, but rather define combinations of flags.

See also: [`combinations`](@ref)
