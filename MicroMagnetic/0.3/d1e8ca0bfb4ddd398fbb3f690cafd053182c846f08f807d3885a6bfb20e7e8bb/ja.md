```
add_exch_bq(sim::AtomisticSim, K::NumberOrArray; name="exch_bq")
```

原子シミュレーション `sim` に二次交換相互作用を追加します。二次交換相互作用は次のように定義されます。

$$
\mathcal{H}_\mathrm{ex} = - \sum_{\langle i, j\rangle} K_{ij} (\mathbf{m}_{i} \cdot \mathbf{m}_{j})^2
$$
