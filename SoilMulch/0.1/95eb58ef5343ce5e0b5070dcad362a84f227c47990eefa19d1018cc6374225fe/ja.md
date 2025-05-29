`cover_fraction(cf, t, tr, cmax, r, γ, tsen)`

作物被覆率を計算します。

# 引数

  * `cf::Float64`: 作物被覆率。
  * `t::Float64`: 時間 [日]。
  * `tr::Float64`: 植物の蒸散。
  * `cmax::Float64`: 最大作物被覆率。
  * `r::Float64`: 被覆率モデルのパラメータ。
  * `γ::Float64`: tsen以降の老化の増加の傾き。
  * `tsen::Float64`: 老化時間。

植物の蒸散が利用できない場合は、EToを使用してください。
