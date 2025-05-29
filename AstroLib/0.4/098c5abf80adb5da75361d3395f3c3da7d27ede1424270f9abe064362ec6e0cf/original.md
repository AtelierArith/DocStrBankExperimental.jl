```
sec2rad(sec) -> radians
```

### Purpose

Convert from seconds to radians.

### Argument

  * `sec`: number of seconds.

### Output

The number of radians corresponding to `sec`.

### Example

```jldoctest
julia> using AstroLib

julia> sec2rad(3600 * 30)
0.5235987755982988
```

### Notes

Use `rad2sec` to convert radians to seconds.
