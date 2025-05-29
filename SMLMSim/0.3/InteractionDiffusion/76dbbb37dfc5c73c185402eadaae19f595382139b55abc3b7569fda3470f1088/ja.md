```
DiffusingEmitter2D{T<:AbstractFloat} <: AbstractDiffusingEmitter
```

拡散シミュレーションのための2Dエミッタタイプで、空間的および時間的情報、さらに分子状態情報を含みます。

# フィールド

  * `x::T`: マイクロメートル単位のx座標
  * `y::T`: マイクロメートル単位のy座標
  * `photons::T`: 放出された光子の数
  * `timestamp::T`: 実際のシミュレーション時間（秒単位）
  * `frame::Int`: フレームレートと露出に基づくカメラフレーム番号
  * `dataset::Int`: データセット識別子
  * `track_id::Int`: 一意の分子識別子
  * `state::Symbol`: 分子状態 (:monomer または :dimer)
  * `partner_id::Union{Int,Nothing}`: リンクされた分子のID（ダイマーの場合）、またはモノマーの場合は何もなし
