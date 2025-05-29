```
StreamingRender(func)
```

An iterable that will run the render function `func`, which takes a single `io` argument that must be passed to the `@render` macro call.

```julia
for bytes in StreamingRender(io -> @render io @component {args...})
    write(http_stream, bytes)
end
```

Or use a `do` block rather than `->` syntax.
