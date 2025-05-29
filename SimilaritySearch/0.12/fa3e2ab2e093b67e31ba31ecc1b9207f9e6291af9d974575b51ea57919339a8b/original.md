```
struct SearchResult
    res::KnnResult  # result struct
    cost::Int32  # number of distances (if algorithm allow it)
    eblocks::Int32 # number of evaluated blocks (whatever it means for some index)
end
```

Response of a typical search knn query
