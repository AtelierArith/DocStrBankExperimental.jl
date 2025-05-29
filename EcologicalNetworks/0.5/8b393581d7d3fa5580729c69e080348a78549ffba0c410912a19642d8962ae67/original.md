```
shortest_path(N::UnipartiteNetwork; nmax::Int64=50)
```

This is not an optimal algorithm *at all*, but it will do given that most ecological networks are relatively small. The optional `nmax` argument is the longest shortest path length you will look for.

In ecological networks, the longest shortest path tends not to be very long, so any value above 10 is probably overdoing it. Note that the default value is 50, which is above 10.
