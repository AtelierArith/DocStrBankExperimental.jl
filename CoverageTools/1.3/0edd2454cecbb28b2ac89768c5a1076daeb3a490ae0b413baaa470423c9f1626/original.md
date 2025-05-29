```
process_cov(filename, folder) -> Vector{CovCount}
```

Given a filename for a Julia source file, produce an array of line coverage counts by reading in all matching .{pid}.cov files.
