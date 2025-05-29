```
LVector(v1::Union{SLArray,LArray}; kwargs...)
```

Creates a 1D copy of v1 with corresponding items in kwargs replaced.

For example:

```
z = LVector(a=1, b=2, c=3);
z2 = LVector(z; c=30)
```
