```
get_sff(tep::TEP)
```

Return the reflection array for front incidence. The array has size `(2, 2, length(theta), length(phi)` for a `TEPscatter` object and `(2, 2, length(theta), length(phi), length(freqs))` for a `TEPperiodic` object.
