```
add_exch(sim::AtomisticSim, J1::NumberOrArray; name="exch", J2=0, J3=0, J4=0)
```

Add exchange interactions to the atomistic simulation `sim`.

$$
\mathcal{H}_\mathrm{ex} = -J \sum_{\langle i, j\rangle} \mathbf{m}_{i} \cdot \mathbf{m}_{j}
$$

### Parameters

  * `J1::NumberOrArray`: The first nearest-neighbor exchange coupling constant. Can be a single number (applied uniformly) or an array with a length equal to the number of first nearest neighbors.
  * `J2, J3, J4` (optional): Exchange coupling constants for second, third, and fourth nearest neighbors, respectively. Each can be a single number or an array with lengths matching their corresponding neighbor counts.
  * `name::String`: Optional identifier for the exchange interaction (default is `"exch"`).

### Usage Examples

To set a uniform exchange coupling for the first nearest neighbors:

```julia
add_exch(sim, 0.1*meV)
```

To set different exchange couplings for multiple neighbor shells:

```julia
Js4 = [0.1*meV, 0.2*meV, 0.3*meV, 0.1*meV, 0.2*meV, 0.3*meV]
add_exch(sim, 0.1*meV, J2=0.2meV, J3=0.0, J4=Js4)
```

#### Notes

If an array is provided for J1, J2, J3, or J4, its length must match the number of corresponding neighbors defined in the system's mesh. Otherwise, an error will be thrown.
