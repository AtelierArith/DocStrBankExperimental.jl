```
BoundedAttributes(attrs; count_limit=nothing, value_length_limit=nothing)
```

This provides a wrapper around attributes (typically `AbstractDict` or `NamedTuple`) to follow the [specification of Attribute](https://opentelemetry.io/docs/reference/specification/common/#attribute).

The following methods from `Base` are defined on `BoundedAttributes` which are then forwarded to the inner `attrs` by default. Feel free to create a PR if you find any method you need is missing:

  * `Base.getindex`
  * `Base.setindex!`
  * `Base.iterate`
  * `Base.length`
  * `Base.haskey`
  * `Base.push!`. Obviously, an error will be thrown when calling on immutable `attrs`s like `NamedTuple`.
