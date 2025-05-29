```
integrate_pixels(
    psf::AbstractPSF,
    pixel_edges_x::AbstractVector,
    pixel_edges_y::AbstractVector,
    emitters::Vector{<:AbstractEmitter};
    support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}} = Inf,
    sampling::Integer=2,
    threaded::Bool=true
)
```

カメラのピクセルに対するPSF強度を、複数のエミッターに対してオプションのサポート領域最適化を用いて統合します。

# 引数

  * `psf`: 統合する点拡散関数
  * `pixel_edges_x`, `pixel_edges_y`: ピクセルエッジ座標を定義する配列
  * `emitters`: 位置情報を持つエミッターのベクター
  * `support`: 各エミッターの計算領域（デフォルト: Inf = 全画像）

      * Realの場合: 各エミッターの周りのマイクロメートル単位の半径
      * Tupleの場合: 明示的な（x*min, x*max, y*min, y*max）マイクロメートル単位（すべてのエミッターに対する固定領域）
  * `sampling`: サブピクセルサンプリング密度（デフォルト: 2）
  * `threaded`: 統合にマルチスレッドを使用するかどうか（デフォルト: true）自動微分フレームワークと一緒に使用する場合はfalseに設定

# 戻り値

  * カメラに一致する次元の統合されたPSF強度の配列
  * 値はすべてのエミッターからの実際の光子数を表します

# 注意事項

  * 結果は個々のエミッターの寄与の合計です（非コヒーレント加算）
  * コヒーレント加算の場合は、`integrate_pixels_amplitude`を使用して複素振幅を合計してください
