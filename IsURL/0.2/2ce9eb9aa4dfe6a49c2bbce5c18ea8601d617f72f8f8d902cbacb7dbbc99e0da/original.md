```
isurl(str)
```

Checks if the given string is an absolute URL.

# Examples

```julia-repl
julia> isurl("https://julialang.org")
true
julia> isurl("mailto:someone@example.com")
true
julia> isurl("/foo/bar")
false
```
