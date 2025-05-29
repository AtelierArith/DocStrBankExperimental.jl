```
DijkstraState(::DijkstraState{T, U}, src) where {T, U} -> DijkstraState{T, U}
```

clean up the DijkstraState to reusue the memory and avoid reallocations
