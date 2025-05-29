```
g = second_order_system(K, τ, ξ)
```

construct a second-order transfer function with gain `K`, time constant `τ`, and damping coefficient `ξ`:

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# example

```jldoctest
K = 1.0
τ = 2.0
ξ = 0.1
g = second_order_system(K, τ, ξ)
# output
         1.0
---------------------
4.0*s^2 + 0.4*s + 1.0
```

# returns

  * `g::TransferFunction`: the second order transfer function. well, (0, 2) order.
