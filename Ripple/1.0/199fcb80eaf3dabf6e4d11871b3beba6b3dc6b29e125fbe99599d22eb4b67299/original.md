```
function read_nfx(fname::String; applygain=true)
```

Read the NFx file `fname` and return a [`NxFile`](@ref).

If `applygain` is `true`, will automatically apply the calculated gain and offset to the data.
