```
create_table(combined_results::OrderedDict; kws...)
```

Create a markdown table of the results loaded from the `load_results` function. If there are two results for a given benchmark, will have an additional column for the comparison, assuming the first revision is one to compare against.

The `formatter` keyword argument generates the column value. It defaults to `TableUtils.format_time`, which prints the median time ± the interquantile range. `TableUtils.format_memory` is also available to print the number of allocations and the allocated memory.
