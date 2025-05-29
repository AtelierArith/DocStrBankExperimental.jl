```
togrep(Z::AbstractZonotope)
```

Return a generator representation of a zonotopic set.

### Input

  * `Z` – zonotopic set

### Output

The same set in generator representation. This fallback implementation returns a `Zonotope`; however, more specific implementations may return other generator representations.
