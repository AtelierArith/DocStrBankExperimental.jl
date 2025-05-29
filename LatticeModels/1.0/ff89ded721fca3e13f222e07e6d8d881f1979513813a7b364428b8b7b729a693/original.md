```
DensityCurrents <: AbstractCurrents
```

Density currents for given state and given hamiltonian.

---

```
DensityCurrents(hamiltonian, state)
```

Constructs a `DensityCurrents` object for given `hamiltonian` and `state`.

## Arguments

  * `hamiltonian`: A `Hamiltonian` object representing the Hamiltonian of the system.
  * `state`: A `Ket` or `Bra` representing the wavefunction or an `Operator` representing the density matrix.

## Example

## Examples

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4);

julia> H0 = tightbinding_hamiltonian(lat); psi = groundstate(H0);

julia> H1 = tightbinding_hamiltonian(lat, field=LandauGauge(0.1));

julia> currents = DensityCurrents(H1, psi)
Density currents for system:
One particle on 16-site SquareLattice in 2D space
```
