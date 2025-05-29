```
save(io::IO, sstr::ScanningStrategy)
save(filename::AbstractString, sstr::ScanningStrategy)
```

Write a definition of the scanning strategy in a self-contained JSON file. You can reload this definition using one of the constructors of [`ScanningStrategy`](@ref).
