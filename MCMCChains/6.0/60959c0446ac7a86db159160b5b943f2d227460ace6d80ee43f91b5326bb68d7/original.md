```
setinfo(c::Chains, n::NamedTuple)
```

Return a new `Chains` object with a `NamedTuple` type `n` placed in the `info` field.

# Example

```julia
new_chn = setinfo(chn, NamedTuple{(:a, :b)}((1, 2)))
```
