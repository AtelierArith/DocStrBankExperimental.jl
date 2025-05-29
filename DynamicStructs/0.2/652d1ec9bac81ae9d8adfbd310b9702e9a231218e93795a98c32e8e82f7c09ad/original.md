```
@dynamic [mutable] struct ... end
```

Define a dynamic struct:

  * Instances of dynamic structs have dynamic properties that can be added/deleted at runtime. These properties are similar to `Any`-typed fields of structs in terms of performance.
  * Fields remain statically typed and accessing them compiles similarly to structs, so performance should not be significantly affected.
  * The macro adds a hidden field for storing dynamic properties with lazy initialization, meaning that the underlying storage is not allocated until the first dynamic property is added.
  * The default constructors of dynamic structs accept keyword arguments for dynamic properties, with a `Base.show` method that reflects this. These are only present if the block is free of any non-field expressions, such as custom constructors.
