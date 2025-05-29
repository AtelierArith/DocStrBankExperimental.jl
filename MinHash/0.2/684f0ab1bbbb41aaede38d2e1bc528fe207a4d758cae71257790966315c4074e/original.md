```
sketch([F=hash], it, s::Integer)
```

Hash every element of iterable `it` using function `F`, and return a `MinHashSketch` containing at most the `s` smallest hashes.

# Examples:

```jldoctest
julia> sketch("ACGDEFG", 3)
MinHashSketch:
 hashes:  3 / 3
 maxhash: 0x3e1b023d3c92ff8f
```

See also: [`update!`](@ref)
