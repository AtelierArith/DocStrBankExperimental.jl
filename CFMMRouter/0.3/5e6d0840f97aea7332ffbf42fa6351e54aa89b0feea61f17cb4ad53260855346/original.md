```
BasketLiquidation(i, Δin)
```

Liquidation objective for the routing problem,

$$
    \Psi_i - \mathbf{I}(\Psi_{-i} + Δ^\mathrm{in}_{-i} = 0, ~ \Psi_i \geq 0),
$$

where `i` is the desired output token and `Δin` is the basket of tokens to be liquidated.
