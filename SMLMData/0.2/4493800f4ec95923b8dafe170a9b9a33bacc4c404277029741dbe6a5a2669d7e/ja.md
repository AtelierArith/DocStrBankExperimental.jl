```
Emitter2DFit{T}(x, y, photons, bg, σ_x, σ_y, σ_photons, σ_bg;
                frame=0, dataset=1, track_id=0, id=0) where T
```

オプションの識別パラメータを持つ2Dローカリゼーションフィット結果の便利なコンストラクタ。

# 引数

## 必須

  * `x::T`: マイクロメートル単位のフィットされたx座標
  * `y::T`: マイクロメートル単位のフィットされたy座標
  * `photons::T`: フィットされたフォトン数
  * `bg::T`: ピクセルあたりのフィットされた背景
  * `σ_x::T`: マイクロメートル単位のx位置の不確実性
  * `σ_y::T`: マイクロメートル単位のy位置の不確実性
  * `σ_photons::T`: フォトン数の不確実性
  * `σ_bg::T`: 背景レベルの不確実性

## オプションのキーワード

  * `frame::Int=0`: 取得シーケンス内のフレーム番号
  * `dataset::Int=1`: 特定の取得/データセットの識別子
  * `track_id::Int=0`: フレーム間でのローカリゼーションをリンクするための識別子
  * `id::Int=0`: データセット内の一意の識別子

# 例

```julia
# 必須パラメータのみでエミッタを作成
emitter = Emitter2DFit{Float64}(
    1.0, 2.0,        # x, y
    1000.0, 10.0,    # photons, background
    0.01, 0.01,      # σ_x, σ_y
    50.0, 2.0        # σ_photons, σ_bg
)

# 特定のフレームとデータセットでエミッタを作成
emitter = Emitter2DFit{Float64}(
    1.0, 2.0, 1000.0, 10.0, 0.01, 0.01, 50.0, 2.0;
    frame=5, dataset=2
)
```
