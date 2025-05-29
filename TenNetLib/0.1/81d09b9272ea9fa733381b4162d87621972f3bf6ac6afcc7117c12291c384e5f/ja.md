```
mutable struct TDVPEngine{T <: Union{ProjMPO,
                                     ProjMPOSum2,
                                     ProjMPO_MPS2,
                                     ProjMPOSum_MPS,
                                     ProjCouplingModel,
                                     ProjCouplingModel_MPS}}

TDVPシミュレーションのための`MPS`状態、`SweepData`、および絶対経過時間を保持します。

  * `sysenv::StateEnvs`: 状態psiと環境PHを保持します。
  * `swdata::SweepData`: 各（フル）スイープ後の履歴データを保持します。
  * `abstime::Float64`: 絶対経過時間。
```
