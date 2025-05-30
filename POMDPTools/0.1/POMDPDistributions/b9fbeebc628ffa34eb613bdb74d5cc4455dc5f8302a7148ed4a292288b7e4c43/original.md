```
Uniform(collection)
```

Create a uniform categorical distribution over a collection of objects.

The objects in the collection must be unique (this is tested on construction), and will be stored in a `Set`. To avoid this overhead, use `UnsafeUniform`.
