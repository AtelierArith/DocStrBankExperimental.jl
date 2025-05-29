```
concurrent(a::PLine, b::PLine, etc)::Bool
concurrent(llist::Vector{PLine})::Bool
```

Test if lines (or a list of lines) are concurrent, i.e., all contain a common point. 
