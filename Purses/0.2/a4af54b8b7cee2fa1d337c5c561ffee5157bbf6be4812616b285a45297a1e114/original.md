```
Purse{T,F<:Tuple,S<:Tuple}
```

Purse with a value and cache.

# Fields

  * `value::T`: the value stored in the purse
  * `cache::S`: the cached values stored as a tuple in the same order as `F`
