```
gen_images(smld::SMLD, psf::AbstractPSF; kwargs...) -> Array{T, 3} where T<:Real
```

指定されたPSFモデルを使用してSMLDデータからカメラ画像を生成します。

# 引数

  * `smld::SMLD`: 単一分子局在データコンテナ
  * `psf::AbstractPSF`: 点拡がり関数モデル

# キーワード引数

  * `dataset::Int=1`: SMLDから使用するデータセット番号
  * `frames=nothing`: 生成する特定のフレーム（デフォルト：smld.n_framesのすべてのフレーム）
  * `support::Union{Real,Tuple{<:Real,<:Real,<:Real,<:Real}}=Inf`: PSFサポート領域のサイズ：

      * `Inf`（デフォルト）：画像全体にわたってPSFを計算（最も正確だが最も遅い）
      * `Real`: 各エミッタの周りに指定された半径（マイクロメートル単位）の円形領域
      * `Tuple{<:Real,<:Real,<:Real,<:Real}`: 明示的な領域を（xmin, xmax, ymin, ymax）としてマイクロメートル単位で指定
  * `sampling::Int=2`: PSF統合のためのスーパサンプリング係数
  * `threaded::Bool=true`: より高速な計算のためにマルチスレッドを有効にする
  * `bg::Float64=0.0`: 背景信号レベル（ピクセルあたりの光子数）
  * `poisson_noise::Bool=false`: ポアソンノイズを適用
  * `camera_noise::Bool=false`: カメラ読み出しノイズを適用（注：この機能はまだ実装されていません）

# 戻り値

  * 次元が[高さ、幅、フレーム数]のカメラ画像の3D配列
  * 要素の型Tはemitter.photonsの型と一致します（通常はFloat64）

# パフォーマンスノート

`support`パラメータについて、有限の半径（通常はPSF幅の3-5倍）を使用することで、精度とパフォーマンスの良いバランスが得られます。例えば、PSF幅が0.15μmの場合、サポート半径は通常0.5-1.0μmで十分です。
