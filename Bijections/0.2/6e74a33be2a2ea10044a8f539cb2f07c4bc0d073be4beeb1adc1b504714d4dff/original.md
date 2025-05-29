```
hasvalue(b::Bijection, y)
```

Checks if `y` is in the image of the Bijection `b`. It is equivalent to checking if the inverse mapping `b.finv` has `y` as a key, so it should as fast as `haskey`.
