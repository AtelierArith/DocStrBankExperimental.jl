```
ξ = damping_coefficient(g)
```

compute the damping coefficient ξ of an order (0, 2) transfer function.

order (0, 2) representation:

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# returns

`ξ::Float64`: the damping coefficient

# examples

```jldoctest
g = 1.0 / (8 * s^2 + 0.8 * s + 2)
damping_coefficient(g)
# output
0.1
```
