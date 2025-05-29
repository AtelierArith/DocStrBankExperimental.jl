```
shrink2cycles!(net::HybridNetwork, unroot::Bool=false)
```

If `net` contains a 2-cycle, collapse the cycle into one edge of length tA + γt1+(1-γ)t2 + tB (see below), and return true. Return false otherwise. A 2-cycle is a set of 2 parallel hybrid edges, from the same parent node to the same hybrid child node.

```
       A                A
       | tA             |
     parent             |
       | \              |
t2,1-γ |  | t1,γ        | tA + γ*t1 + (1-γ)*t2 + tB
       | /              |
     hybrid             |
       | tB             |
       B                B
```

If any of the lengths or gammas associated with a 2-cycle are missing, the combined length is missing. If γ is missing, branch lengths are calculated using γ=0.5.

If `unroot` is false and the root is up for deletion, it will be kept only if it is has degree 2 or more. If `unroot` is true and the root is up for deletion, it will be kept only if it has degree 3 or more. A root node with degree 1 will be deleted in both cases.
