```
function multi_product(g1::Graph{F,W}, g2::Graph{F,W}, c1=F(1), c2=F(1)) where {F,W,C}
```

Returns a graph representing the multi product `c1*g1 * c2*g2`. If `g1 == g2`, it will return a graph representing `c1*c2 * (g1)^2` with `Power(2)` operator.

# Arguments:

  * `g1`:  first computational graph
  * `g2`:  second computational graph
  * `c1`:  first scalar multiple (defaults to 1).
  * `c2`:  second scalar multiple (defaults to 1).
