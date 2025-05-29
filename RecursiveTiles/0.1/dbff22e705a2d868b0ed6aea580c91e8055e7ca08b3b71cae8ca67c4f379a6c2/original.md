```
@scheme f g h1 h2 ...
```

A macro to construct a nested `ExtendScheme` of the form `ExtendScheme(ExtendScheme(Scheme(f, g), h1), h2)` by forming a base (`Scheme(f, g)`), then wrapping with `ExtendScheme(s, h)` until all trailing `h`'s have been exhausted.

# Examples

```jldoctest
julia> (@scheme sum last first) == ExtendScheme(Scheme(sum, last), first)
true

julia> (@scheme sum last first last first) == ExtendScheme(ExtendScheme(ExtendScheme(Scheme(sum, last), first), last), first)
true
```
