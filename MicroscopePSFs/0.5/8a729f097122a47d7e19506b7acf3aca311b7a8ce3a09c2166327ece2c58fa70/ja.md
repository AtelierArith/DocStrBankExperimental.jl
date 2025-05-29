```
integrate_pixels(
    psf::AbstractPSF,
    camera::AbstractCamera,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセル上で複数のエミッターのPSF強度を統合し、オプションのサポート領域最適化を行います。このバージョンは明示的なピクセルエッジの代わりにカメラオブジェクトを受け取ります。

# 引数

  * `psf`: 統合する点拡散関数
  * `camera`: ピクセルエッジを定義するカメラジオメトリ
  * `emitters`: 位置情報を持つエミッターのベクター
  * `support`: 各エミッターの計算領域（デフォルト: Inf = フルイメージ）
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合にマルチスレッドを使用するかどうか（デフォルト: true）

# 戻り値

  * カメラに一致する次元の統合されたPSF強度の配列
  * 値はすべてのエミッターからの実際の光子数を表します
