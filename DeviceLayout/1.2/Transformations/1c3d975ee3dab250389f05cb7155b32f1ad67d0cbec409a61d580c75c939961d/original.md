```
mag(f::Translation)
```

Return the magnification (uniform scaling factor) for `f`, if it is well defined.

Throws a `DomainError` if `f` does not preserve angles ("scaling" depends on direction).
