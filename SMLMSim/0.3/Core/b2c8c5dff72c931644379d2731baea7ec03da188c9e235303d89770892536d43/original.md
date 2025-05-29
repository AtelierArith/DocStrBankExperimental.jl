```
get_track(smld::BasicSMLD, id::Int)
```

Return a new SMLD containing only emitters with the specified track_id.

# Arguments

  * `smld::BasicSMLD`: The original SMLD
  * `id::Int`: Track ID to filter by

# Returns

  * `BasicSMLD`: New SMLD containing only emitters from the specified track

# Example

```julia
# Get all emitters belonging to track 5
track_smld = get_track(smld, 5)
```
