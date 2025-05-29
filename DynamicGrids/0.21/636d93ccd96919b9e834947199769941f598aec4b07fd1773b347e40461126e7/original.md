```
SetGrid{R,W}(f)
```

Apply a function `f` to fill whole grid/s.

Broadcasting is a good way to update values.

## Example

This example simply sets grid `a` to equal grid `b`:

```jldoctest
using DynamicGrids
rule = SetGrid{:a,:b}() do a, b
    b .= a
end

# output
SetGrid{:a,:b}(
    f = var"#1#2"
)
```
