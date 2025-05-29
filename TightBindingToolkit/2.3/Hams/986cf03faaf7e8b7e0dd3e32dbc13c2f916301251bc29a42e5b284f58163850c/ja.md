`Hamiltonian` は、与えられた `UnitCell` と `BZ` に対応する一般的な運動量空間ハミルトニアンを表すデータ型です（BdG ハミルトニアンの場合は 2 つのユニットセル）。

# 属性

  * `H           :: Array{Matrix{ComplexF64}}`: `BZ` の k-点のグリッドに対応するハミルトニアン行列の配列。
  * `bands       :: Array{Vector{Float64}}`: `BZ` の k-点のグリッドに対応するバンドスペクトルの配列。
  * `states      :: Array{Matrix{ComplexF64}}`: `BZ` の k-点のグリッドに対応するバンド波動関数の配列。
  * `bandwidth   :: Tuple{Float64, Float64}` : バンド構造における最小エネルギーと最大エネルギーのタプル。
  * `is_BdG      :: Bool` : ハミルトニアンが BdG ハミルトニアンであるか、純粋なホッピングハミルトニアンであるか。

この構造体は次のように初期化します。

```julia
Hamiltonian(uc::UnitCell, bz::BZ) --> Hopping Hamiltonian
Hamiltonian(uc_hop::UnitCell, uc_pair::UnitCell, bz::BZ) --> BdG Hamiltonian
```
