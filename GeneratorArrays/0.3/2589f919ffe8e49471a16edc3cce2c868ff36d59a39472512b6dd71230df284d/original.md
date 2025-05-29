```
array(g::<generator or iterator>)
```

Construct a wrapped object of type `GeneratorArray(g)`. The object provides the `AbstractArray` interface in, but does not support `setindex!`.

The wrapped object must have a size `(IteratorSize(g) == HasShape())`.
