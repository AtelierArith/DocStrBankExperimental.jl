```
 function obj_to_ptr(obj)
```

Returns the hexadecimal representation of the address of the object `obj`. It **only** works with mutable objects.  If `obj` is immutable, then `0x0` will be returned.
