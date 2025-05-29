```
prime_ideals_over(O::AlgAssRelOrd, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> Vector{AlgAssRelOrdIdl}
```

$$
O
$$

上のすべての素イデアルを返します。ここで、$p$は`base_ring(O)`の素イデアルです。
