```
integrate_pixels_amplitude(
    psf::AbstractPSF, 
    camera::AbstractCamera, 
    emitter::AbstractEmitter;
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上でPSFの複素振幅を統合し、オプションのサポート領域最適化を行います。

このバージョンは、明示的なピクセルエッジの代わりにカメラオブジェクトを受け取ります。

# 引数

  * `psf::AbstractPSF`: 統合する点拡散関数
  * `camera::AbstractCamera`: マイクロメートル単位でピクセルエッジを定義するカメラジオメトリ
  * `emitter::AbstractEmitter`: カメラに対してマイクロメートル単位で位置を持つエミッタ
  * `support`: 計算する領域（デフォルト: Inf = フルイメージ）

      * Realの場合: エミッタの周りの半径（マイクロメートル単位）
      * Tupleの場合: 明示的な（x*min, x*max, y*min, y*max）（マイクロメートル単位）
  * `sampling::Integer=2`: 各次元のピクセルあたりのサンプル数
  * `threaded::Bool=true`: 統合のためにマルチスレッドを使用するかどうか

# 戻り値

  * 複素振幅の行列
  * 配列のインデックスは左上のピクセルに対して[1,1]から始まります

参照: [`integrate_pixels`](@ref), [`AbstractPSF`](@ref)
