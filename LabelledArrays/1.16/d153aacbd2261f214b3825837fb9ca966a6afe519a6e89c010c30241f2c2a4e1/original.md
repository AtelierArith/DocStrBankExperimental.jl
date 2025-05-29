```
SLVector(v1::SLArray; kwargs...)
```

Creates a copy of v1 with corresponding items in kwargs replaced.

For example:

```
ABCD = @SLArray (2,2) (:a,:b,:c,:d);
B = ABCD(1,2,3,4);
B2 = SLArray(B; c=30 )
```
