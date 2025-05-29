```julia
Coordinates(itr)

```

Convert the argument, which can be any iterable object, to coordinates.

Specifically,

  * `Coordinate` and `Nothing` are passed through *as is*,
  * 2- or 3-element tuples of finite real numbers or strings are interpreted as coordinates,
  * `()`, and tuples with non-finite numbers become `nothing` (representing empty lines).

The resulting coordinates are checked for dimension consistency.

## Examples

The following are equivalent:

```julia
Coordinates((x, 1/x) for x in -5:5)
Coordinates(x == 0 ? () : (x, 1/x) for x in -5:5)
Coordinates(x == 0 ? nothing : Coordinate((x, 1/x)) for x in -5:5)
```

Use `enumerate` to add 1, 2, … for the `x`-axis to an existing set of `y` coordinates:

```julia
Coordinates(enumerate([1, 4, 9]))
```
