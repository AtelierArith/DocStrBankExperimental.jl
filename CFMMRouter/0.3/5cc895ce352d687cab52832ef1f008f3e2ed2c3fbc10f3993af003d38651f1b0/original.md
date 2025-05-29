```
Swap(i, j, δ, n)
```

Swap objective for the routing problem with `n` tokens:

$$
    \Psi_i - \mathbf{I}(\Psi_{[n]\setminus\{i,j\}} = 0,\; {\Psi_j = -\delta})
$$

where `i` is the desired output token, `j` is the input token, and `δ` the amount input. Note that this is shorthand for a BasketLiquidation objective where `Δin` is a one-hot vector. 
