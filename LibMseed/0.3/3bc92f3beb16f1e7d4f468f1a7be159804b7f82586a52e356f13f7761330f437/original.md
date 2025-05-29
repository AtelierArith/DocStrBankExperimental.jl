```
NanosecondDateTime(nstime)
```

Construct a `NanosecondDateTime` from an `Int64`.  This represents the integer number of nanoseconds since the epoch of `1970-01-01T00:00:00.000000000`. Hence the range of dates which can be represented is `1677-09-21T00:12:43.145224192 - 2262-04-11T23:47:16.854775807`.

# Example

```
julia> NanosecondDateTime(100)
NanosecondDateTime("1970-01-01T00:00:00.000000100")
```
