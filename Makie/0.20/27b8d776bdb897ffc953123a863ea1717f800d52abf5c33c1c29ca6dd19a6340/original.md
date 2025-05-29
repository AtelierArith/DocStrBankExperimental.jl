```
broadcast_foreach(f, args...)
```

Like broadcast but for foreach. Doesn't care about shape and treats Tuples && StaticVectors as scalars. This method is meant for broadcasting across attributes that can either have scalar or vector / array form. An example would be a collection of scatter markers that have different sizes but a single color. The length of an attribute is determined with `attr_broadcast_length` and elements are accessed with `attr_broadcast_getindex`.
