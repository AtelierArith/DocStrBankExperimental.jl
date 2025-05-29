```
load_scanning_strategy(io::IO) -> ScanningStrategy
load_scanning_strategy(filename::AbstractString) -> ScanningStrategy
```

Create a `ScanningStrategy` object from the definition found in the JSON file `io`, or from the JSON file with path `filename`. See also [`load_scanning_strategy`](@ref).
