```
generic_state(::AbstractSite, ::String)
```

Do not call directly. It returns a local state corresponding to the string, this is tried first before trying specifically defined states.

The default implementation returns the first state for "0", the second for "1" and so on.

This should be overloaded if necessary when defining new site types. It may return an error when not needed.
