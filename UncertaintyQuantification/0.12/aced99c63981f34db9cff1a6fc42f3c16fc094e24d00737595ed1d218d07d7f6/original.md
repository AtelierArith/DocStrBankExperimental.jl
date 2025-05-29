```
dimensions(sr::SpectralRepresentation) -> Int
```

Returns the number of dimensions (frequencies) in the given `SpectralRepresentation` instance.

# Arguments

  * `sr::SpectralRepresentation`: An instance of the `SpectralRepresentation` struct.

# Returns

An integer representing the number of dimensions (frequencies).

# Example

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
num_dimensions = dimensions(sr)
```
