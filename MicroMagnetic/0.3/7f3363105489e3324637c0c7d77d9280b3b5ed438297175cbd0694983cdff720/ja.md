```
add_demag(sim::AtomisticSim; name="demag", Nx=0, Ny=0, Nz=0 )
```

システムに双極子相互作用を追加します。

$$
\mathcal{H}_{\mathrm{d}}=-\frac{\mu_0 \mu_s^2}{4 \pi} \sum_{i<j} \frac{3\left(\mathbf{m}_i \cdot \hat{\mathbf{r}}_{i j}\right)\left(\mathbf{m}_j \cdot \hat{\mathbf{r}}_{i j}\right)-\mathbf{m}_i \cdot \mathbf{m}_j}{r_{i j}^3}
$$
