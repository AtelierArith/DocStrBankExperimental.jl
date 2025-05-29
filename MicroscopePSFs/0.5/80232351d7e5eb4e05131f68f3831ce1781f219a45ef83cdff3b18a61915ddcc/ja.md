```
integrate_pixels_amplitude(
    psf::AbstractPSF,
    camera::AbstractCamera,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上で複数のエミッタに対してPSFの複素振幅を統合します。オプションのサポート領域最適化を使用できます。このバージョンでは、明示的なピクセルエッジの代わりにカメラオブジェクトを使用します。

# 引数

  * `psf`: 統合する点拡散関数
  * `camera`: ピクセルエッジを定義するカメラジオメトリ
  * `emitters`: 位置情報を持つエミッタのベクター
  * `support`: 各エミッタの計算領域（デフォルト: Inf = フルイメージ）
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合にマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * 統合された複素振幅の配列
  * 値はコヒーレントに合計された場の寄与を表します
