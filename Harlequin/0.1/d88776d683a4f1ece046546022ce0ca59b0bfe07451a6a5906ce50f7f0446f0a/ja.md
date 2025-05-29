```
compute_z_and_group!(dest_baselines, vectors, baseline_lengths, destriping_data::DestripingData{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
compute_z_and_group!(dest_baselines, baseline_lengths, destriping_data::DestripingData{T, O}, obs_list::Vector{Observation{T}}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
```

行列 $A$ の KurkiSuonio2009 の式 (25) における適用を計算します。結果は一連のベースラインであり、`dest_baselines` に保存されます（要素の型が `T` の配列）。2 つの形式は `vec` パラメータの有無のみが異なります：存在しない場合、`obs.tod` の値が使用されます。
