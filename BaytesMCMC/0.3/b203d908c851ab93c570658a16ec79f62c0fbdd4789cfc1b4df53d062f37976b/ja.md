```julia
struct PhaseTune{T<:Tuple}
```

現在のSamplingPhaseに関する情報。

# フィールド

  * `update::BaytesCore.Updater`: 現在のイテレーションが更新を必要とするかどうかのブール値。
  * `iter::BaytesCore.Iterator`: フェーズ内の現在のイテレーションをカウントします。
  * `counter::BaytesCore.Iterator`: MCMCフェーズ ~ counter = スライス/名前/イテレーションの現在のサイクル。
  * `slices::Vector{Int64}`: 各フェーズでのMCMCイテレーションのベクター。
  * `name::Tuple`: サンプリングフェーズの名前。
  * `iterations::Vector{Int64}`: 総イテレーションのカウント。
  * `window::Vector{Int64}`: Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ()の適応フェーズにおけるサイクルのカウント。すなわち、1-5-1は1ウィンドウ初期化、5適応、1探索を意味します。
  * `buffer::Vector{Int64}`: Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ()の適応フェーズにおける各サイクルのイテレーションのカウント。すなわち、50-25-50は1回50、5回25*i、iは1:5、1回50を意味します。
