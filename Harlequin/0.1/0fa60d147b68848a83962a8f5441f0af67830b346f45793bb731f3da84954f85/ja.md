```
compute_z_and_subgroup!(dest_baselines, vec, baseline_lengths, destriping_data::DestripingData{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
compute_z_and_subgroup!(dest_baselines, baseline_lengths, destriping_data::DestripingData{T, O}, obs::Observation{T}; comm=nothing, unseen=NaN) where {T, O <: Healpix.Order}
```

行列 $A$ の KurkiSuonio2009 の式 (25) における適用を計算します。結果は一連のベースラインであり、`dest_baselines` に保存されます（要素の型が `T` の配列）。2 つの形式は `vec` パラメータの有無のみが異なります：存在しない場合、`obs.tod` の値が使用されます。

この関数は単一の観測にのみ作用します。観測の配列に適用したい場合は、[`compute_z_and_group!`](@ref) を使用してください。
