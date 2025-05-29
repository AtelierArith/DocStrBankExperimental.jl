```
g = first_order_system(K, τ)
```

construct a first-order transfer function with gain `K` and time constant `τ`:

$$
g(s)=\frac{K}{\tau s+1}
$$

# example

```jldoctest
K = 1.0
τ = 3.0
g = first_order_system(K, τ)
# output
    1.0
-----------
3.0*s + 1.0
```

# returns

  * `g::TransferFunction`: the first order transfer function. well, (0, 1) order.
