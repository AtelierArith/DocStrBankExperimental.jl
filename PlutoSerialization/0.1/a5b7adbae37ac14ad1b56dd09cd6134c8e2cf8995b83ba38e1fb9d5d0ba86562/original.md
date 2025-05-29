```
deserialize(filename::AbstractString)
deserialize(io::IO)
```

Deserialize `filename` or `io` into a Julia object using Julia's serialization, but correctly handle Pluto's workspace modules.
