```
allow_unicode(allowed::Bool; temporary::Bool=false) -> Bool
```

Set whether unicode characters are allowed in pretty printing and returns the previous value. If `temporary` is `true`, then the change is only active for the current worker and session. Otherwise, the change is permanently saved in the preferences. A permanent change will always override a temporary change.

This function may behave arbitrarily if called from within the scope of a `with_unicode` do-block.

See also [`is_unicode_allowed`](@ref) and [`with_unicode`](@ref).
