```
setrecord!(logger::Logger, rec::Type{R}) where {R<:Record}
```

Sets the record type for the logger.

# Arguments

  * `logger::Logger`: the logger to set.
  * `rec::Record`: A `Record` type to use for logging messages (ie: `DefaultRecord`).
