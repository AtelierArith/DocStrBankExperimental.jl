```
deletemetadata!(x, key::AbstractString)
```

Delete metadata for object `x` for key `key` and return `x` (if metadata for `key` is not present do not perform any action). Throw an error if `x` does not support metadata deletion.
