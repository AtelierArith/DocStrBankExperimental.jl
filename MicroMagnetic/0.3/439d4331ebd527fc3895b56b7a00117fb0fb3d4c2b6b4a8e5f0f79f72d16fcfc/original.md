```
add_dmi(sim::AtomisticSim, Dfun::Function; name="dmi")
```

Add spatial DMI to the system. The DMI is defined as

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle}  \mathbf{D}_{i j} \cdot\left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

where $\mathbf{D}_{i j}$ is the DM vector.  The function should accept the indices `(i, j, k)` representing the position of the spin  on the mesh and return an **array**. The length of this array should be half the number of neighbors.

For example, for a `CubicMesh`, the function should return an array `[(D1, D2, D3), (D4, D5, D6), (D4, D5, D6)]`, where:

  * `(D1, D2, D3)` represents the DM vector between the site at `(i, j, k)` and the site at `(i+1, j, k)`,
  * `(D4, D5, D6)` represents the DM vector between the site at `(i, j, k)` and the site at `(i, j+1, k)`,
  * `(D7, D8, D9)` represents the DM vector between the site at `(i, j, k)` and the site at `(i, j, k+1)`.

The array length corresponds to half the number of neighbors, because exchange interactions are considered only in the positive direction (i.e., the interactions with neighboring sites in increasing index directions).

#### Examples:

```julia
function spatial_bulk_DMI(i, j, k)
    Dx = i < 10 ? 0.1meV : 0.2meV
    Dy = 0.1meV
    Dz = 0.3meV
    return [(Dx, 0, 0), (0, Dy, 0), (0, 0, Dz)]  # Returns an array
end

add_dmi(sim, spatial_bulk_DMI)
```
