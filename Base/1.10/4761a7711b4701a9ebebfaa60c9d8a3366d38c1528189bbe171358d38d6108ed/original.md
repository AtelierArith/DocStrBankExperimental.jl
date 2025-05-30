```
instances(T::Type)
```

Return a collection of all instances of the given type, if applicable. Mostly used for enumerated types (see `@enum`).

# Example

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
