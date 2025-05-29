```
safe_stereo_hydrogen!(mol::SimpleMolGraph, v::Integer) -> Bool
```

Rearrange stereocenter properties to safely remove stereo hydrogen nodes and return the hydrogen node index.

This function is called inside `rem_vertex!` and `rem_vertices!` functions to safely remove hydrogen nodes while preserving stereocenter information.
