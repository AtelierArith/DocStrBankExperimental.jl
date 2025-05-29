```
compute!(logger::Logbook, data::AbstractVector)
compute!(notebooks::Vector{Logbook}, data::Vector{AbstractVector})
```

Computes statistics for `logger` (or a vector of `logger`s) using `data`, which is usually a vector of fitnesses. All calculations are done in place, so the `logger` records will be updated.
