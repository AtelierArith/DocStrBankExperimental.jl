```
MinHashSketch
```

Holds the N smallest hashes of an iterable. Construct from a `MinHasher`.

# Examples

```jldoctest
julia> x = MinHashSketch(update!(MinHasher(10), 1:1000))
MinHashSketch:
 hashes:  10 / 10
 maxhash: 0x0214ce7a1c004d40

julia> length(x)
10
```
