```
ReadonlyCollection(collection::DataCollection)
```

Modification of `collection` is not viable, as it is read-only.

# Example Occurrence

```julia-repl
julia> lockedcollection = DataCollection(SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128)), "config" => SmallDict{String, Any}("locked" => true)))
julia> write(lockedcollection)
ERROR: ReadonlyCollection: The data collection unnamed#298 is locked
Stacktrace: [...]
```
