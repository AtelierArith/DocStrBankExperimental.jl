```
drawline(func::Function, ci1::CartesianIndex{2}, ci2::CartesianIndex{2}, eachstep::Bool=false)
```

At each step along the line from `ci1` to `ci2` call `func` with a single argument, the row, column coordinates of the pixel as a `Tuple{Int, Int}`.

If `eachstep=true` then `func` is called once when the row changes and once when the column changes.  When `eachstep=false` then `func` is called less frequently and both row and col may change between calls.
