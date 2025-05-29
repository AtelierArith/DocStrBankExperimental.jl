```
issymplectic(form::Symplecticform, x::AbstractMatrix; atol=0.0, rtol=atol)
issymplectic(x::Symplectic; atol=0.0, rtol=atol)
```

Return whether or not an input matrix is symplectic. Keyword arguments `atol` and `rtol` can be called to determine absolute and relative tolerances of the check, respectively.
