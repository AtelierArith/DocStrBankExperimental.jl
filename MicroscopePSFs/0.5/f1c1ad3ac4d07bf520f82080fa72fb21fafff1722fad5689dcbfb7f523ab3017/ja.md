```
integrate_pixels_amplitude(
    psf::VectorPSF,
    camera::AbstractCamera,
    emitter::AbstractEmitter;
    sampling::Integer=2,
    threaded::Bool=true
)
```

VectorPSFの偏光成分を保持する振幅統合の特化版。

# 引数

  * `psf`: VectorPSFインスタンス
  * `camera`: ピクセルエッジを定義するカメラジオメトリ
  * `emitter`: 位置情報を持つエミッタ
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合にマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * 次元[y, x, pol]の統合された複素振幅の3D配列。ここで、polインデックス1 = Ex、polインデックス2 = Ey
