```
trainable(x::Layer) -> NamedTuple
```

This may be overloaded to make optimisers ignore some fields of every `Layer`, which would otherwise contain trainable parameters.

!!! warning
    This is very rarely required. Fields of `struct Layer` which contain functions, or integers like sizes, are always ignored anyway. Overloading `trainable` is only necessary when some arrays of numbers are to be optimised, and some arrays of numbers are not.


The default is `Functors.children(x)`, usually a NamedTuple of all fields, and `trainable(x)` must contain a subset of these.
