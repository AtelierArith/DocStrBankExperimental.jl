```
get_scene_id(scene)
```

Lookup the unique identifier for the provided scene.

# Parameters

  * `scene`: The name of the Sentinel scene to lookup.

# Returns

The unique identifier for downloading the provided scene.

# Example

```julia
julia> scene = "S2B_MSIL2A_20200804T183919_N0500_R070_T11UPT_20230321T050221";

julia> get_scene_id(scene)
"29f0eaaf-0b15-412b-9597-16c16d4d79c6"
```
