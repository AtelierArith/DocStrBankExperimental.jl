```
function linear_combination(g1::Graph{F,W}, g2::Graph{F,W}, c1, c2) where {F,W}
```

Returns a graph representing the linear combination `c1*g1 + c2*g2`. If `g1 == g2`, it will return a graph representing `(c1+c2)*g1`. Graphs `g1` and `g2` must have the same orders.

# Arguments:

  * `g1`  first computational graph
  * `g2`  second computational graph
  * `c1`  first scalar multiple
  * `c2`  second scalar multiple
