```
isrelativeurl(str)
```

Checks if the given string is a relative URL.

julia> isrelativeurl("../path/to/directory") true julia> isrelativeurl("./**file**") true julia> isrelativeurl("foo:bar") false
