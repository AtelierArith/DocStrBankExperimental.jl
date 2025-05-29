```
multirank(specs::AbstractArray{<:Spectrum})::Float64
```

A single number that compares the low and high energy portions of the spectra for similarity.  A `multirank(...)` score of zero means all the spectra are very similar and a large number means very different. A high score suggests that one or more of the spectra may suffer from additional low energy absorption due to surface roughness, an obstruction, sample tilt or other.
