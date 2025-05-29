```
to_standard_normal_space!(sr::SpectralRepresentation, df::DataFrame) -> Nothing
```

Transforms the random phase angles in the given `DataFrame` from a uniform distribution to a standard normal distribution.

# Arguments

  * `sr::SpectralRepresentation`: An instance of the `SpectralRepresentation` struct.
  * `df::DataFrame`: A `DataFrame` containing the random phase angles to be transformed.

# Returns

Nothing. The `DataFrame` is modified in place.

# Example

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
samples = sample(sr, 5)
to_standard_normal_space!(sr, samples)
```
