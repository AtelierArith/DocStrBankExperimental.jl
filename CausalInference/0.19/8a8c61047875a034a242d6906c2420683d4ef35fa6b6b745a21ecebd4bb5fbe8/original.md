```
backdoor_criterion(g::AbstractGraph, u::Integer, v::Integer, Z; verbose = false)
```

Test that given directed graph `g`, no node in `Z` is descendant of `u` and `Z` d-separates `u` from `v`  in the subgraph that only has the backdoors of `u` left (outgoing edges of `u` removed).

If so, the causal effect of `u` on `v` is identifiable and is given by the formula:

```
∑{z∈Z} p(v | u, z)p(z)
```

In the linear Gaussian model, find `E[Y | X = x, Z = z] = α + βx + γ'z` and obtain `E[Y | do(x)] = α + βx + γ'E[Z].
