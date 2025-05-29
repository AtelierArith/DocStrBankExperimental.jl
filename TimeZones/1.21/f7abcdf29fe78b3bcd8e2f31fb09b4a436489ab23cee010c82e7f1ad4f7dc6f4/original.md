```
build(version::AbstractString; force::Bool=false) -> Nothing
```

Builds the TimeZones package with the specified tzdata `version` and `regions`. The `version` is typically a 4-digit year followed by a lowercase ASCII letter (e.g. "2025b"). The `force` flag is used to re-download tzdata archives.

!!! warning
    This function is *not* thread-safe and meant primarily for experimentation.

