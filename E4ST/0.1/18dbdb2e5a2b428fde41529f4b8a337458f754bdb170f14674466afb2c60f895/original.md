```
mod_rank(::Type{Modification}) ->
```

Returns the rank of the Modification.  Rank is the order in which the type of mod should be applied relative to other types of mods.  Defaults to 0, where 1 would come after other mods and -1 would come before.  Ranks is defined for mod types. 
