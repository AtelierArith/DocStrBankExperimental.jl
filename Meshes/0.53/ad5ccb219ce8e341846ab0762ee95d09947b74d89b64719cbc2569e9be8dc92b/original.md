```
Shadow(dims)
```

Project the geometry or domain onto the given `dims`, producing a "shadow" of the original object.

## Examples

```julia
Shadow(:xy)
Shadow("xz")
Shadow(1, 2)
Shadow((1, 3))
```
