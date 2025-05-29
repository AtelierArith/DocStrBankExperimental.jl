```
get_dep_param(r_1::Real, r_2::Real, r_m::Real)
get_dep_param(; r_1::Real, r_2::Real, r_m::Real, r_im::Real = r_m, r_r::Real = r_m)
```

[`DepolarisingParameters`](@ref) オブジェクトを返し、脱極化パウリノイズモデルをパラメータ化します。

# 引数

  * `r_1::Real`: 単一量子ビットゲートのエンタングルメント不完全性、すべての3つの非単位パウリエラー確率の合計。
  * `r_2::Real`: 二量子ビットゲートのエンタングルメント不完全性、すべての15の非単位パウリエラー確率の合計。
  * `r_m::Real`: 測定エラー確率。
  * `r_im::Real`: 中間回路測定アイドルエンタングルメント不完全性。
  * `r_r::Real`: 中間回路リセットエラー確率。
  * `combined::Bool`: パウリX、Y、Z基底のSPAMノイズを同じものとして扱うかどうか。
