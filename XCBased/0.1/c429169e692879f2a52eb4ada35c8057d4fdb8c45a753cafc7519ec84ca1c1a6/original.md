```
connection_has_error(conn:: XCBConnection) -> Union{Cint, Nothing}
```

Returns one of the constants listed in [`XCBConnectionError`](@ref), or `nothing` if there is no error.
