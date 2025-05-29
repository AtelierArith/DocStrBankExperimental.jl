```
TokenStream(
    code::S,
    flag_set::FlagSet{FP}
) where {S<:AbstractString, FP<:FlagPair}
```

A dictionary whose keys are the flag IDs, and whose values are vectors of `Int`s indicating the nestedness of the flag.
