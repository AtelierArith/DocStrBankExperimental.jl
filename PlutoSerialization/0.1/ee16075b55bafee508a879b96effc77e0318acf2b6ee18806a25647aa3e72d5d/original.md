```
serialize(filename::AbstractString, object)
serialize(io::IO, object)
```

Save the given `object` to `filename` or `io` using Julia's serialization, but additionally handle Pluto's workspace modules such that the saved data can be `deserialized` in a new session.
