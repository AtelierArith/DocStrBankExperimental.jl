```
add_dmi(sim::AtomisticSim, Dij::Array{<:Real, 2}; name="dmi")
```

システムにDzyaloshinskii-Moriya相互作用（DMI）を追加します。これは次のように定義されます：

$$
\mathcal{H}_\mathrm{dmi} = \sum_{\langle i, j\rangle} \mathbf{D}_{ij} \cdot \left(\mathbf{m}_{i} \times \mathbf{m}_{j}\right)
$$

ここで、$\mathbf{D}_{ij}$はDMIベクトルです。`Dij`配列はサイズが`(3, mesh.n_ngbs)`であり、各隣接サイト間のDMIベクトルを表します。例えば、`CubicMesh`の場合、`Dij`配列はDMIベクトルの配列`[D1, D2, D3, D4, D5, D6]`である必要があります。ここで：

  * `D1`はサイト`(i, j, k)`とサイト`(i-1, j, k)`間のDMIベクトルです。
  * `D2`はサイト`(i, j, k)`とサイト`(i+1, j, k)`間のDMIベクトルです。
  * `D3`はサイト`(i, j, k)`とサイト`(i, j-1, k)`間のDMIベクトルです。
  * `D4`はサイト`(i, j, k)`とサイト`(i, j+1, k)`間のDMIベクトルです。
  * `D5`はサイト`(i, j, k)`とサイト`(i, j, k-1)`間のDMIベクトルです。
  * `D6`はサイト`(i, j, k)`とサイト`(i, j, k+1)`間のDMIベクトルです。

### 例

```julia
# CubicMeshのためのバルクDMIを定義
D = 0.1 * meV
Dij = hcat([-D, 0, 0],  # (i-1, j, k)のためのDMIベクトル
           [D, 0, 0],   # (i+1, j, k)のためのDMIベクトル
           [0, -D, 0],  # (i, j-1, k)のためのDMIベクトル
           [0, D, 0],   # (i, j+1, k)のためのDMIベクトル
           [0, 0, -D],  # (i, j, k-1)のためのDMIベクトル
           [0, 0, D])   # (i, j, k+1)のためのDMIベクトル

add_dmi(sim, Dij)
```
