```
get_num_tracks(smld::BasicSMLD)
```

Return the number of unique tracks (based on track_id) in the SMLD.

# Arguments

  * `smld::BasicSMLD`: The SMLD to analyze

# Returns

  * `Int`: Number of unique track IDs

# Example

```julia
# Get the number of tracks
n_tracks = get_num_tracks(smld)
```
