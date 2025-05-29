```
update_binned_map!(vec, skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
update_binned_map!(skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
update_binned_map!(skymap::PolarizedMap{T, O}, hitmap::Healpix.Map{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T <: Real, O <: Healpix.Order}
```

Eqs. (18), (19), および (20) を適用して、TOD から I、Q、および U の値を計算し、結果を `skymap` と `hitmap` に保存します。

3 つのバージョンは、TOD キャリブレーションデータのソースによって異なります：

  * `vec` パラメータが存在する場合（最初の形式）、それが `obs.tod`（2 番目の形式）の代わりに使用されます。
  * `obs`（単一の [`Observation`](@ref) オブジェクト）の代わりに、配列 `obs_list` を渡すことができます（3 番目の形式）。この配列内のすべての要素が `skymap` と `hitmap` を更新するために使用されます。
