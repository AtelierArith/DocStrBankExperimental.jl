```
rebuild(A::AbstractDimArray, data, [dims, refdims, name, metadata]) => AbstractDimArray
rebuild(A::AbstractDimArray; kw...) => AbstractDimArray
```

Rebuild and `AbstractDimArray` with some field changes. All types that inherit from `AbstractDimArray` must define this method if they have any additional fields or alternate field order.

Implementations can discard arguments like `refdims`, `name` and `metadata`.

Additional arguments can be added to the keyword argument method. 

For readability it is preferable to use keyword versions for any more than a few arguments.
