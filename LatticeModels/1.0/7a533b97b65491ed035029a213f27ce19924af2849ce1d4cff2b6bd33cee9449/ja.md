```
OperatorBuilder([T, ]sys, [; field, auto_hermitian, auto_pbc_field])
OperatorBuilder([T, ]lat, [internal; field, auto_hermitian])

与えられたシステムまたは格子のための `OperatorBuilder` を構築します。

## 引数

  * `T`: 行列要素の型。デフォルトは `ComplexF64` です。
  * `sys`: システムを表す `System` オブジェクト。
  * `lat`: 演算子が定義されている格子。
  * `internal`: 内部自由度の基底。

## キーワード引数

  * `field`: ホッピング演算子に使用するゲージ場。デフォルトは `NoField()` で、これはゼロの磁場に対応します。
  * `auto_hermitian`: 演算子のエルミート共役を自動的に追加するかどうか。デフォルトは `false` です。
  * `auto_pbc_field`: 格子の周期境界条件に自動的に場を適応させるかどうか。デフォルトは `true` です。

## 例

```

jldoctest julia> using LatticeModels

julia> l = SquareLattice(5, 5);

julia> builder = OperatorBuilder(l, field=LandauGauge(0.1), auto*hermitian=true) OperatorBuilder(field=LandauGauge(0.1), auto*hermitian=true) System: 2D空間の25サイトのSquareLattice上の1粒子

julia> hx = Bravais[1, 0]; hy = Bravais[0, 1];

julia> for site in l; builder[site, site + hx] = builder[site, site + hy] = 1; end

julia> H = Hamiltonian(builder) Hamiltonian(dim=25x25) System: 2D空間の25サイトのSquareLattice上の1粒子 25×25 SparseArrays.SparseMatrixCSC{ComplexF64, Int64} で80の格納エントリを持つ: ⎡⠪⡢⡈⠢⡀⠀⠀⠀⠀⠀⠀⠀⠀⎤ ⎢⠢⡈⠠⡢⡈⠢⡀⠀⠀⠀⠀⠀⠀⎥ ⎢⠀⠈⠢⡈⠊⡠⡈⠢⡀⠀⠀⠀⠀⎥ ⎢⠀⠀⠀⠈⠢⡈⠪⠂⡈⠢⡀⠀⠀⎥ ⎢⠀⠀⠀⠀⠀⠈⠢⡈⠪⡢⠈⠢⡀⎥ ⎢⠀⠀⠀⠀⠀⠀⠀⠈⠢⡀⠪⡢⡀⎥ ⎣⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠀⠈⠀⎦

julia> H == tightbinding_hamiltonian(l, field=LandauGauge(0.1)) true ```
