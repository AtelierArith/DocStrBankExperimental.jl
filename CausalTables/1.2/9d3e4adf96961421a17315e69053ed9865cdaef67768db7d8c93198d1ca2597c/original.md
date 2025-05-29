```
summarize(o::CausalTable)
```

Summarizes the data in a `CausalTable` object according to the NetworkSummary objects stored in its `summaries` attribute.

# Arguments

  * `o::CausalTable`: The `CausalTable` object to be summarized.

# Returns

  * A new `CausalTable` object with the original data merged with the summarized data.
