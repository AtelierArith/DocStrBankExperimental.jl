```
integrate_pixels_amplitude(
    psf::SplinePSF,
    camera::AbstractCamera,
    emitter::AbstractEmitter;
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上でPSF振幅（複素数）を統合します。

# 引数

  * `psf`: SplinePSFインスタンス
  * `camera`: カメラのジオメトリ
  * `emitter`: 位置情報を持つエミッタ
  * `support`: 計算する領域（デフォルト: Inf = 全画像）

      * Realの場合: エミッタの周りのマイクロメートル単位の半径
      * Tupleの場合: マイクロメートル単位の明示的な（x*min, x*max, y*min, y*max）
  * `sampling`: 統合精度のためのサブピクセルサンプリング密度
  * `threaded`: 統合のためにマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * 次元が[ny, nx]の統合されたPSF複素振幅の配列

# 注意事項

  * 3D SplinePSF（z_rangeが定義されている場合）には、z座標を持つエミッタが必要です。
