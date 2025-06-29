```
LognormalParameters
```

対数正規分布のランダムパウリノイズモデルをパラメータ化します。

# フィールド

  * `params::Dict{Symbol, Any}`: 以下に説明するノイズパラメータの辞書。
  * `noise_name::String`: データを保存するためのノイズパラメータ名。

# パラメータ

  * `r_1::Float64`: 平均単一量子ビットゲートのエンタングルメント不完全性、すべての3つの非単位パウリエラー確率の合計。
  * `r_2::Float64`: 平均二量子ビットゲートのエンタングルメント不完全性、すべての15の非単位パウリエラー確率の合計。
  * `r_m::Float64`: 平均測定エラー確率。
  * `r_im::Float64`: 平均中間回路測定アイドルエンタングルメント不完全性。
  * `r_r::Float64`: 平均中間回路リセットエラー確率。
  * `r_1_std_log::Float64`: 単一量子ビットゲートのエンタングルメント不完全性の対数の近似標準偏差。
  * `r_2_std_log::Float64`: 二量子ビットゲートのエンタングルメント不完全性の対数の近似標準偏差。
  * `r_m_std_log::Float64`: 測定エラー確率の対数の近似標準偏差。
  * `r_im_std_log::Float64`: 中間回路測定アイドルエンタングルメント不完全性の対数の近似標準偏差。
  * `r_r_std_log::Float64`: 中間回路リセットエラー確率の対数の近似標準偏差。
  * `seed::UInt64`: ノイズを生成するために使用されるランダムシード。
  * `combined::Bool`: パウリX、Y、Z基底のSPAMノイズを同じものとして扱うかどうか。
