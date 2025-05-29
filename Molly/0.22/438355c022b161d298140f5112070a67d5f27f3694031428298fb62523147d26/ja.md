```
PeriodicTorsion(; periodicities, phases, ks, proper)
```

四つの原子間の周期的なねじれ角。

`phases` はラジアンで表されます。ポテンシャルエネルギーは次のように定義されます。

$$
V(\phi) = \sum_{n=1}^N k_n (1 + \cos(n \phi - \phi_{s,n}))
$$
