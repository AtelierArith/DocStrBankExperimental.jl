```
get_header(con::SeisCon, name::String)
```

Gets the metadata summary, `name`, from every `BlockScan` in `con`. Column 1 contains the minimum value of `name` within the block, and Column 2 contains the maximum value of `name` within the block. Src/Rec scaling is not applied.

To get source coordinate pairs as an array, see `get_sources`. 

# Example

trace = get_header(s, "TraceNumber")
