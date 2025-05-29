```
LocalOperatorCurrents <: AbstractCurrents
```

与えられた状態と与えられたハミルトニアンのための局所演算子（例：スピン）電流。

---

```
LocalOperatorCurrents(hamiltonian, state, op)
```

与えられた `hamiltonian` と `state` のための `DensityCurrents` オブジェクトを構築します。

## 引数

  * `hamiltonian`: システムのハミルトニアンを表す `Hamiltonian` オブジェクト。
  * `state`: 波動関数を表す `Ket` または `Bra`、または密度行列を表す `Operator`。
  * `op`: 局所（オンサイト）演算子；`Operator` またはその行列。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4); site1, site2 = lat[1:2];

julia> H0 = qwz(lat); psi = groundstate(H0);

julia> H1 = qwz(lat, field=LandauGauge(0.1));

julia> op = [1 0; 0 -1];            # スピン演算子

julia> currents = LocalOperatorCurrents(H1, psi, op)
Currents of Operator(Spin(1/2))
 1   0
 0  -1
For system:
One particle on (16-site SquareLattice in 2D space) ⊗ Spin(1/2)

julia> op2 = one(SpinBasis(3//2));  # 無効な演算子

julia> LocalOperatorCurrents(H1, psi, op2)
ERROR: ArgumentError: Operator must be defined on the internal basis of the Hamiltonian.
[...]
```
