```
AttributeRecord <: Record
```

A `Record` which stores its properties as `Attribute`s for lazy evaluation.

Calling `getproperty` or iterating will evaluate and cache the properties accessed.
