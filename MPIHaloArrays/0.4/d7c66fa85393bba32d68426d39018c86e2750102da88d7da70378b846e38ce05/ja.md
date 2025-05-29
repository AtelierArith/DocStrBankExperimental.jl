```
neighbor(p::CartesianTopology, i_offset::Int, j_offset::Int, k_offset::Int)
```

オフセット `(i,j,k)` に基づいて隣接ランクを見つけます。これはMPIのバージョンではなく、従来の配列インデックスの規則に従っているため、`i_offset=1` は配列インデックスで上にシフトします。

# 引数

  * `p`: CartesianTopology 型
  * `i_offset`: `i` 方向のオフセット
  * `j_offset`: `j` 方向のオフセット
  * `k_offset`: `k` 方向のオフセット

# 例:

```julia
# 両方の次元で周期境界を持つ4x4のドメインを作成
P = CartesianTopology((4,4), (true, true))

# ihi 隣接を見つける
ihi = neighbor(P,+1,0,0)

# 上の ihi コーナー隣接 (ihi と jhi 側)
ihijhi_corner = neighbor(P,+1,+1,0)
```
