```
integrate_pixels_amplitude(
    psf::VectorPSF,
    camera::AbstractCamera,
    emitters::Vector{<:AbstractEmitter};
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセルに対してPSFの複素振幅を複数のエミッターにわたって統合します。偏光成分を保持するVectorPSF用の特別なバージョンです。

# 引数

  * `psf`: VectorPSFインスタンス
  * `camera`: ピクセルのエッジを定義するカメラのジオメトリ
  * `emitters`: 位置情報を持つエミッターのベクター
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合にマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * 次元[y, x, pol]の統合された複素振幅の3D配列。ここで、polインデックス1 = Ex、polインデックス2 = Ey

# 注意事項

  * 結果は、個々のエミッターの場の寄与のコヒーレントな和です。
