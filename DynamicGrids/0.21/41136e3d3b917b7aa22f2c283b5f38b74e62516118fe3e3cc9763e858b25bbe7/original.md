```
add!(data::WritableGridData, x, I...)
```

Add the value `x` to a grid cell.

## Example useage

```jldoctest
using DynamicGrids
rule = SetCell{:a}() do data, a, cellindex
    dest, is_inbounds = inbounds(data, (jump .+ cellindex)...)

    # Update spotted cell if it's on the grid
    is_inbounds && add!(data[:a], state, dest...)
end

# output
SetCell{:a,:a}(
    f = var"#1#2"
)
```
