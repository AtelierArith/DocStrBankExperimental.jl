```
SLVector(v1::SLArray; kwargs...)
```

Creates a 1D copy of v1 with corresponding items in kwargs replaced.

For example:

```
z = SLVector(a=1, b=2, c=3);
z2 = SLVector(z; c=30)
```
