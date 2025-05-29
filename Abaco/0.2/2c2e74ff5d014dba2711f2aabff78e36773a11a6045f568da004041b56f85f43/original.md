```
ingest(abaco, ts, ne, values)
```

Adds the input variables include in the dictionary `values`.

```julia
    # now timestamp 
    ts = nowts()

    # short name of network node
    ne = "trento.castello"

    values = Dict(
        "x" => 23.2,
        "y" => 100
    )
    ingest(abaco, ts, ne, values)
```
