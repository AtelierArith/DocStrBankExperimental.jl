```
@cached_call f(args; kwargs)
```

Caches the result of `f(args; kwargs)` to disk and returns the result. The next time `f(args; kwargs)` is called with the same values of `args` and `kwargs` the cached result is returned and `f` is not called again. Splatting is not yet supported.

Restrictions on `f` apply: it must not mutate its arguments or access/mutate globals. These assumptions will not be checked and if violated could mean that an incorrect result is returned.

Functions are differentiated by name only, meaning that changing the definition and rerunning `@cached_call` will return the wrong result.
