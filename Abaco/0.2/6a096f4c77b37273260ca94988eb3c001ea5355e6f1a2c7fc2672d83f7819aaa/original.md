```
ingest!(abaco, payload)
```

Adds the input variables included in the `payload` dictionary.

The Dict `msg` must contains the keys `ts` and `ne` and a numbers of other keys managed as input variables.

This function modifies the `payload` dictionary: `ne` and `ts` keys are popped out.  

```julia
    payload = Dict(
        "ts" => nowts(),
        "ne" => "trento.castello",
        "x" => 23.2,
        "y" => 100
    )
    ingest!(abaco, ts, ne, payload)
```
