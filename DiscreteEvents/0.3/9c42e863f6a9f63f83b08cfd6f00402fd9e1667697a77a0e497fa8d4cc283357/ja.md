```
Clock{AC} <: AbstractClock
```

グローバルおよびスレッドローカルクロックに使用される仮想クロック構造。

# フィールド

  * `id::Int`: クロック識別番号 1: マスタークロック, > 1: パラレルクロック,
  * `ac::AC`: id == 1 の場合: [`Vector{ClockChannel}`](@ref ClockChannel), それ以外: [`Ref{ActiveClock}`](@ref ActiveClock),
  * `state::ClockState`: クロックの状態,
  * `time::Float64`: クロックの時間,
  * `unit::FreeUnits`: 時間単位,
  * `end_time::Float64`: シミュレーションの終了時間,
  * `Δt::Float64`: サンプリング時間, ティック間のタイムステップ,
  * `sc::Schedule`: クロックの[`Schedule`](@ref) (イベント、条件付きイベント、サンプリング),
  * `processes::Dict{Any, Prc}`: 登録された`Prc`es,
  * `channels::Vector{Channel}`: 登録された(アクター)チャネル,
  * `tn::Float64`: 次のタイムステップ,
  * `tev::Float64`: 次のイベント時間,
  * `evcount::Int`: イベントカウンタ,
  * `scount::Int`: サンプルカウンタ
