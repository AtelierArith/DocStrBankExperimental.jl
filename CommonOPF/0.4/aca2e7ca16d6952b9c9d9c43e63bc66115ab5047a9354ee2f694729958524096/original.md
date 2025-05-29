```
next_bus_above_with_outdegree_more_than_one(g::MetaGraphsNext.MetaGraph, b::String)
```

Find the next bus above `b` with outdegree more than one. If none are found than `nothing` is returned. Throws an error if a bus with indegree > 1 is found above `b`.
