```
dcc_send_data(src::AbstractString, filename; type = nothing)
dcc_send_data(writer::Function, data, filename; type = nothing)
```

Convert string into the format expected by the Download component. `writer` function must have signature `(io::IO, data)`

# Examples

Sending string content

```julia
text_data = "this is the test"
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_string(text_data, "text.txt")
end
```

Sending `DataFrame` in `CSV` format

```julia
using DataFrames, CSV
...
df = DataFrame(...)
callback!(app, Output("download", "data"), Input("download-btn", "n_clicks"), prevent_initial_call = true) do n_clicks
    return dcc_send_string(CSV.write, df, "df.csv")
end
```
