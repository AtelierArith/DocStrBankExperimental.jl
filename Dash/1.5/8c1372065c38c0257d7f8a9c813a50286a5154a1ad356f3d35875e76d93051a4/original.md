```
dcc_send_bytes(src::AbstractVector{UInt8}, filename; type = nothing)
dcc_send_bytes(writer::Function, data, filename; type = nothing)
```

Convert vector of bytes into the format expected by the Download component. `writer` function must have signature `(io::IO, data)`

# Examples

Sending binary content

```julia
file_data = read("path/to/file")
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_bytes(file_data, "filename.fl")
end
```

Sending `DataFrame` in `Arrow` format

```julia
using DataFrames, Arrow
...
df = DataFrame(...)
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_bytes(Arrow.write, df, "df.arr")
end
```
