```
state_vectors(state::ReplicaState)
state_vectors(sim::PMCSimulation)
```

`state` からの構成ベクトルの `r×s` `AbstractMatrix` を返すか、[`solve(::ProjectorMonteCarloProblem)`](@ref) の結果を返します。ベクトルは、結果のコレクションをインデックスでアクセスすることで取得でき、行インデックスはレプリカインデックスに対応し、列インデックスはスペクトル状態インデックスに対応します。

他に [`ProjectorMonteCarloProblem`](@ref)、[`Rimu.PMCSimulation`](@ref)、[`Rimu.SingleState`](@ref)、[`Rimu.ReplicaState`](@ref)、[`Rimu.SpectralState`](@ref) を参照してください。
