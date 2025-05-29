```
eliminate!(G::AbstractGraph, v::Integer, c_map::Dict{Int, Int})
```

Connect all the neighbours of v together before removing v from G. 

The dictionary `c_map` mapping vertices of 'G' to their cliqueness is updated inplace  accordingly.
