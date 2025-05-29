```
with_unicode(f::Function, allowed::Bool=true)
```

Temporarily set whether unicode characters are allowed in pretty printing during the execution of `f`. This is useful for e.g. running doctests independently on the user preference.

`with_unicode` is expected to be called in the following way:

```julia
with_unicode([allowed]) do
   # code that should be executed with unicode allowed/disallowed
end
```

See also [`allow_unicode`](@ref) and [`is_unicode_allowed`](@ref).
