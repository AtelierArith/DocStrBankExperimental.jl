```
τ = time_constant(g)
```

compute the time constant τ of an order (0, 1) or order (0, 2) transfer function.

order (0, 1) representation:

$$
g(s)=\frac{K}{\tau s+1}
$$

order (0, 2) representation:

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# returns

`τ::Float64`: the time constant.

# examples

```jldoctest
g = 4 / (6 * s + 2)
time_constant(g)
# output 
3.0

g = 1.0 / (8 * s^2 + 0.8 * s + 2)
time_constant(g) 
# output
2.0
```
