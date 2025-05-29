```
add_dmi(sim::AtomisticSim, Dij::Array{<:Real, 2}; name="dmi")
```

Add Dzyaloshinskii-Moriya Interaction (DMI) to the system, defined as:

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle} \mathbf{D}_{ij} \cdot \left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

where $\mathbf{D}_{ij}$ is the DMI vector. The `Dij` array should have size `(3, mesh.n_ngbs)` and represents the DMI vectors between each pair of neighboring sites. For example, for a `CubicMesh`, the `Dij` array should be an array of DMI vectors `[D1, D2, D3, D4, D5, D6]`, where:

  * `D1` is the DMI vector between the site at `(i, j, k)` and the site at `(i-1, j, k)`,
  * `D2` is the DMI vector between the site at `(i, j, k)` and the site at `(i+1, j, k)`,
  * `D3` is the DMI vector between the site at `(i, j, k)` and the site at `(i, j-1, k)`,
  * `D4` is the DMI vector between the site at `(i, j, k)` and the site at `(i, j+1, k)`,
  * `D5` is the DMI vector between the site at `(i, j, k)` and the site at `(i, j, k-1)`,
  * `D6` is the DMI vector between the site at `(i, j, k)` and the site at `(i, j, k+1)`.

### Examples

```julia
# Define bulk DMI for a CubicMesh
D = 0.1 * meV
Dij = hcat([-D, 0, 0],  # DMI vector for (i-1, j, k)
           [D, 0, 0],   # DMI vector for (i+1, j, k)
           [0, -D, 0],  # DMI vector for (i, j-1, k)
           [0, D, 0],   # DMI vector for (i, j+1, k)
           [0, 0, -D],  # DMI vector for (i, j, k-1)
           [0, 0, D])   # DMI vector for (i, j, k+1)

add_dmi(sim, Dij)
```
