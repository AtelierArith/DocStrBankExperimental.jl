```
get_tracks(smld::BasicSMLD)
```

Return a vector of SMLD objects, one for each unique track (based on track_id).

# Arguments

  * `smld::BasicSMLD`: The original SMLD

# Returns

  * `Vector{BasicSMLD}`: Vector of SMLD objects, one per track

# Example

```julia
# Get all tracks as separate SMLD objects
track_smlds = get_tracks(smld)

# Access the first track
first_track = track_smlds[1]
```
