```
integrate_pixels_amplitude(
    psf::AbstractPSF,
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上で複数のエミッターのためにPSF複素振幅を統合し、オプションのサポート領域最適化を行います。

# 引数

  * `psf`: 統合する点拡散関数
  * `pixel_edges_x`, `pixel_edges_y`: ピクセルエッジ座標を定義する配列
  * `emitters`: 位置情報を持つエミッターのベクター
  * `support`: 各エミッターのために計算する領域（デフォルト: Inf = フルイメージ）
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合のためにマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * 統合された複素振幅の配列
  * 値はコヒーレントに合成された場の寄与を表します

# 注意事項

  * 結果は個々のエミッターの場の寄与のコヒーレントな合計です
  * 非コヒーレントな加算を行うには、`abs2.(integrate_pixels_amplitude(...))`を使用するか、`integrate_pixels`を使用してください
