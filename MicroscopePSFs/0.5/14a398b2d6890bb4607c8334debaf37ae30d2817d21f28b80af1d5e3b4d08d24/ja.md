```
integrate_pixels(
    psf::AbstractPSF, 
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitter::AbstractEmitter; 
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上でPSF強度を統合し、オプションのサポート領域最適化を行います。

指定された領域内の各ピクセルについて、指定されたサンプリング密度を使用してPSF強度を数値的に統合します。物理座標はカメラに対して相対的で、(0,0)は左上隅にあります。PSFとエミッタの両方がサポートしている場合、z座標を自動的に処理します。

# 引数

  * `psf::AbstractPSF`: 統合する点拡散関数
  * `pixel_edges_x::AbstractVector`: マイクロメートル単位のピクセルのX座標エッジ
  * `pixel_edges_y::AbstractVector`: マイクロメートル単位のピクセルのY座標エッジ
  * `emitter::AbstractEmitter`: カメラに対してマイクロメートル単位で位置を持つエミッタ
  * `support`: 計算する領域（デフォルト: Inf = 全画像）

      * Realの場合: エミッタの周りの半径（マイクロメートル単位）
      * Tupleの場合: 明示的な(x*min, x*max, y*min, y*max)（マイクロメートル単位）
  * `sampling::Integer=2`: 各次元のピクセルあたりのサンプル数
  * `threaded::Bool=true`: 統合にマルチスレッドを使用するかどうか 自動微分フレームワークと一緒に使用する場合はfalseに設定

# 戻り値

  * `Matrix{T}`: 統合された強度で、Tはemitter.photonsの型と一致
  * 配列は[y,x]としてインデックス付けされ、[1,1]は左上隅のピクセル
  * 値はエミッタの光子値に基づく各ピクセルの実際の光子数を表します

# 例

```julia
# 100nmのピクセルを持つ20x20カメラのためのピクセルエッジを作成
pixel_edges_x = pixel_edges_y = 0:0.1:2.0
emitter = Emitter2D(1.0, 1.0, 1000.0)  # (1μm, 1μm)に1000光子のエミッタ
psf = GaussianPSF(0.15)  # σ = 150nm

# 全画像に対して計算
pixels = integrate_pixels(psf, pixel_edges_x, pixel_edges_y, emitter)

# エミッタの0.5μm半径内のみ計算
pixels_roi = integrate_pixels(psf, pixel_edges_x, pixel_edges_y, emitter, support=0.5)
```

参照: [`integrate_pixels_amplitude`](@ref), [`AbstractPSF`](@ref)
