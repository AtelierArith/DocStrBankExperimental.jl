```
xcb_connect(display_name:: Union{AbstractString, Nothing} = nothing) -> XCBConnection
```

Connect to an X server at `display_name`. If `display_name` is `nothing`, XCB will use the `DISPLAY` environment variable. The function throws an [`XCBConnectionError`](@ref) if one occurs.
