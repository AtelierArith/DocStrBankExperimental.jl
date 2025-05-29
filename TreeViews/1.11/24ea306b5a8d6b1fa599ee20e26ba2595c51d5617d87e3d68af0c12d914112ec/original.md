```
treelabel(io::IO, x, mime = MIME"text/plain"())
```

Prints `x`'s tree header to `io`. Like with `Base.show` there are also methods with `mime::AbstractString` and no `mime` argument at all (which falls back to `MIME"text/plain"()`). Please only overload the `treelabel(io::IO, x, mime::MIME)` form.
