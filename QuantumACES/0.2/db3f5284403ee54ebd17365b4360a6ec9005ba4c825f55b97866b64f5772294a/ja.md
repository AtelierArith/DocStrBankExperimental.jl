```
get_log_param(r_1::Real, r_2::Real, r_m::Real, std_log::Real; seed::Union{UInt64, Nothing} = nothing, combined::Bool = false)
get_log_param(; r_1::Real, r_2::Real, r_m::Real, r_im::Real = r_m, r_r::Real = r_m, r_1_std_log::Real, r_2_std_log::Real, r_m_std_log::Real, r_im_std_log::Real = r_m_std_log, r_r_std_log::Real = r_m_std_log, seed::Union{UInt64, Nothing} = nothing, combined::Bool = false)
```

[`LognormalParameters`](@ref) オブジェクトを返し、対数正規分布に従うランダムパウリノイズモデルをパラメータ化します。

すべての標準偏差を `std_log` として指定することができます。

# 引数

  * `r_1::Float64`: 平均単一量子ビットゲートの絡み合い不完全性、すべての3つの非単位パウリ誤差確率の合計。
  * `r_2::Float64`: 平均二量子ビットゲートの絡み合い不完全性、すべての15の非単位パウリ誤差確率の合計。
  * `r_m::Float64`: 平均測定誤差確率。
  * `r_im::Float64`: 平均中間回路測定アイドル絡み合い不完全性。
  * `r_r::Float64`: 平均中間回路リセット誤差確率。
  * `r_1_std_log::Float64`: 単一量子ビットゲートの絡み合い不完全性の対数の近似標準偏差。
  * `r_2_std_log::Float64`: 二量子ビットゲートの絡み合い不完全性の対数の近似標準偏差。
  * `r_m_std_log::Float64`: 測定誤差確率の対数の近似標準偏差。
  * `r_im_std_log::Float64`: 中間回路測定アイドル絡み合い不完全性の対数の近似標準偏差。
  * `r_r_std_log::Float64`: 中間回路リセット誤差確率の対数の近似標準偏差。
  * `seed::UInt64`: ノイズを生成するために使用されるランダムシード。
  * `combined::Bool`: パウリX、Y、およびZ基底のSPAMノイズを同じものとして扱うかどうか。
