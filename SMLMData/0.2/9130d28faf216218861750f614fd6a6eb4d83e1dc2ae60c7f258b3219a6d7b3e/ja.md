```
Emitter2DFit{T} <: AbstractEmitter
```

不確実性と時間/追跡情報を伴うフィッティングされた2Dローカリゼーション結果を表します。

# フィールド

  * `x::T`: マイクロメートル単位のフィッティングされたx座標
  * `y::T`: マイクロメートル単位のフィッティングされたy座標
  * `photons::T`: フィッティングされた光子の数
  * `bg::T`: ピクセルあたりのフィッティングされた背景光子数
  * `σ_x::T`: マイクロメートル単位のx位置の不確実性
  * `σ_y::T`: マイクロメートル単位のy位置の不確実性
  * `σ_photons::T`: 光子数の不確実性
  * `σ_bg::T`: ピクセルあたりの背景の不確実性
  * `frame::Int`: 取得シーケンス内のフレーム番号
  * `dataset::Int`: 特定の取得/データセットの識別子
  * `track_id::Int`: フレーム間でのローカリゼーションをリンクするための識別子 (0 = リンクされていない)
  * `id::Int`: データセット内のユニークな識別子
