```
labelCanonically(Fs::Vector{T})::Vector{T} where {T <: Flag}
```

Labels all Flags in `Fs` canonically. If two Flags are isomorphic, this function should return the same Flag.
