```
either(:left, bool_condition, "right")
```

If `bool_condition` is true, it returns the right value, wrapped into [Identity](@ref). Else returns left side, wrapped into [Const](@ref).

## Example

```jldoctest
either(:left, 1 < 2, "right") == Identity("right")
```
