```
unpack(belief_history::Vector{<:GaussianBelief};
    dims::Vector{Int}=[])
```

Given a history of beliefs, return an unpacked (time steps, state dim)-sized array of predicted means and a (time steps, state dim, state dim)-sized array of covariances. One can optionally specify dimensions indices dims to output reduced state information.
