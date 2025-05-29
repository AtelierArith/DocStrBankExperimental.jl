```
function read_nsx(fname::String)
```

Read the NSx file `fname` and return a [`NxFile`](@ref).

If `applygain` is `true`, will automatically apply the calculated gain and offset to the data.
