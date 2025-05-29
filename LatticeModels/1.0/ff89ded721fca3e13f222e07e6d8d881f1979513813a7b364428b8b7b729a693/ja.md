```
DensityCurrents <: AbstractCurrents
```

与えられた状態と与えられたハミルトニアンのための密度電流。

---

```
DensityCurrents(hamiltonian, state)
```

与えられた `hamiltonian` と `state` のための `DensityCurrents` オブジェクトを構築します。

## 引数

  * `hamiltonian`: システムのハミルトニアンを表す `Hamiltonian` オブジェクト。
  * `state`: 波動関数を表す `Ket` または `Bra`、または密度行列を表す `Operator`。

## 例

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4);

julia> H0 = tightbinding_hamiltonian(lat); psi = groundstate(H0);

julia> H1 = tightbinding_hamiltonian(lat, field=LandauGauge(0.1));

julia> currents = DensityCurrents(H1, psi)
Density currents for system:
One particle on 16-site SquareLattice in 2D space
```
