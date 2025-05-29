```
add_dmi(sim::AtomisticSim, D::Real; name="dmi", type="bulk")
```

システムにDMIを追加します。`type`は「bulk」または「interfacial」にすることができます。DMIは次のように定義されます。

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle}  \mathbf{D}_{i j} \cdot\left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

ここで、$\mathbf{D}_{i j}$はDMベクトルです。バルクDMIの場合、$\mathbf{D}_{i j} = D \hat{r}_{ij}$、インターフェイシャルDMIの場合、$\mathbf{D}_{i j} = D \hat{r}_{ij} \times \hat{z}$です。

例:

```julia
   J = 0.1 * meV
   add_dmi(sim, 0.01*J, type="bulk")
```
