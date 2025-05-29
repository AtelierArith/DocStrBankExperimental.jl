```
add_dmi(sim::AtomisticSim, D::Real; name="dmi", type="bulk")
```

Add DMI to the system. `type` could be "bulk" or "interfacial". The DMI is defined as

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle}  \mathbf{D}_{i j} \cdot\left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

where $\mathbf{D}_{i j}$ is the DM vector. For the bulk dmi $\mathbf{D}_{i j} = D \hat{r}_{ij}$ and for interfacial dmi $\mathbf{D}_{i j} = D \hat{r}_{ij} \times \hat{z}$.

Examples:

```julia
   J = 0.1 * meV
   add_dmi(sim, 0.01*J, type="bulk")
```
