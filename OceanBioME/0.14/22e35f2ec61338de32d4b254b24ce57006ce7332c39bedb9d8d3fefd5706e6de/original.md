```
ZeroNegativeTracers(; exclude = ())
```

Construct a modifier that zeroes any negative tracers excluding those listed in `exclude`.

!!! danger "Tracer conservation"
    This method is *not* recommended as a way to preserve positivity of tracers since it does not conserve the total tracer.

