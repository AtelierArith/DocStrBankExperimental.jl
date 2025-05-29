```
LocalOperatorCurrents <: AbstractCurrents
```

Local operator (e. g. spin) currents for given state and given hamiltonian.

---

```
LocalOperatorCurrents(hamiltonian, state, op)
```

Constructs a `DensityCurrents` object for given `hamiltonian` and `state`.

## Arguments

  * `hamiltonian`: A `Hamiltonian` object representing the Hamiltonian of the system.
  * `state`: A `Ket` or `Bra` representing the wavefunction or an `Operator` representing the density matrix.
  * `op`: A local (on-site) operator; either an `Operator` or a matrix of such.

## Example

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4); site1, site2 = lat[1:2];

julia> H0 = qwz(lat); psi = groundstate(H0);

julia> H1 = qwz(lat, field=LandauGauge(0.1));

julia> op = [1 0; 0 -1];            # Spin operator

julia> currents = LocalOperatorCurrents(H1, psi, op)
Currents of Operator(Spin(1/2))
 1   0
 0  -1
For system:
One particle on (16-site SquareLattice in 2D space) ⊗ Spin(1/2)

julia> op2 = one(SpinBasis(3//2));  # Invalid operator

julia> LocalOperatorCurrents(H1, psi, op2)
ERROR: ArgumentError: Operator must be defined on the internal basis of the Hamiltonian.
[...]
```
