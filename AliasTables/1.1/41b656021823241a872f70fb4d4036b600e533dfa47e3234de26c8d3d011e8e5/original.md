```
sample(x::T, at::AliasTable{T, I}) -> I
```

Sample from `at` using the seed `x`.

If `x` is chosen uniformly at random from the set of all values representable by `T` then the output will be a random sample from the distribution represented by `at`. The mapping is deterministic and not pseudo-random so for patterned input `x` the output will be patterned as well.

See also [`AliasTable`](@ref), [`AliasTables.probabilities`](@ref)
