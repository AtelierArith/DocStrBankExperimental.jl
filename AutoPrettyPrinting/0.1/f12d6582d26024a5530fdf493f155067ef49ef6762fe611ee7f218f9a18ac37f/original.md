```
repr_pretty([mime], x; context=nothing)
```

If `istextmime(mime)` is `true`, returns an `AbstractString` containing the representation of `x` in the requested `mime` type rendered with the `AutoPrettyPrinting.pprint` method. 

Otherwise returns `repr(mime, x; context)`.

If `mime` is not provided, defaults to `MIME"text/plain"`.
