```
abundances(cache::CachedEcosystem, tm::Unitful.Time)
```

Function to extract abundances for an ecosystem, `cache`, at a certain point in time, `tm`. If the abundances for that time are missing from the ecosystem, then the function checks on disk for the last saved version and simulates forward.
