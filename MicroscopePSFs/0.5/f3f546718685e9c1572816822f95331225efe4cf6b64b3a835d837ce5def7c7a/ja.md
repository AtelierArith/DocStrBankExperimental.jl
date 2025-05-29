```
SplinePSF(psf::AbstractPSF; 
          lateral_range::Float64=2.0,
          axial_range::Float64=1.0,
          lateral_step::Float64=0.05,
          axial_step::Float64=0.1,
          order::Integer=3)
```

自動的に計算されたサンプリング範囲を持つSplinePSFを作成します。

# 引数

  * `psf`: サンプリングするソースPSF
  * `lateral_range`: ミクロン単位の横（xy）サンプリング範囲の半幅
  * `axial_range`: ミクロン単位の軸方向（z）サンプリング範囲の半幅
  * `lateral_step`: 横（xy）サンプリングのステップサイズ（デフォルト: 0.05µm = 50nm）
  * `axial_step`: 軸方向（z）サンプリングのステップサイズ（デフォルト: 0.1µm = 100nm）
  * `order`: 補間の次数（デフォルト: 3は三次）

# 戻り値

  * `SplinePSF`: 入力PSFのタイプに応じて2Dまたは3DのスプラインPSF

# 例

```julia
# デフォルトのサンプリングパラメータでスプラインPSFを作成
scalar_psf = ScalarPSF(1.4, 0.532, 1.518)
spline_psf = SplinePSF(scalar_psf)  # デフォルトの範囲とステップサイズを使用
```
