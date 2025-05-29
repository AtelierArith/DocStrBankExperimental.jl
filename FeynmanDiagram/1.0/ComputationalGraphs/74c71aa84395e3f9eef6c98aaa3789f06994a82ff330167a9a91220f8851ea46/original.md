```
function linear_combination(g1::FeynmanGraph{F,W}, g2::FeynmanGraph{F,W}, c1, c2) where {F,W}
```

Returns a graph representing the linear combination `c1*g1 + c2*g2`. If `g1 == g2`, it will return a graph representing `(c1+c2)*g1` Feynman Graphs `g1` and `g2` must have the same diagram type, orders, and external vertices.

# Arguments:

  * `g1`  first Feynman graph
  * `g2`  second Feynman graph
  * `c1`:  first scalar multiple (defaults to 1).
  * `c2`:  second scalar multiple (defaults to 1).
