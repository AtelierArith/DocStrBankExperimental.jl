```
add_exch_bq(sim::AtomisticSim, K::NumberOrArray; name="exch_bq")
```

Add biquadratic exchange interaction to the atomistic simulation `sim`. The biquadratic exchange interaction is defined as

$$
\mathcal{H}_\mathrm{ex} = - \sum_{\langle i, j\rangle} K_{ij} (\mathbf{m}_{i} \cdot \mathbf{m}_{j})^2
$$
