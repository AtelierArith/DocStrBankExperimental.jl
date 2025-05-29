```
function psis_ess(
    weights::AbstractVector{T<:Real},
    r_eff::AbstractVector{T}
) -> AbstractVector{T}
```

PSISサンプルの（近似的な）有効サンプルサイズを計算します。これはVehtari et al. 2019の修正を使用しています。これは、提案分布とターゲット分布のK-Lダイバージェンスを測定するESSのエントロピーベースの定義を使用します。

# 引数

  * `weights`: PSISから導出された正規化された重要度サンプリング重みのセット。
  * `r_eff`: PSISサンプルが導出されたMCMCチェーンの相対効率。

`?relative_eff`を参照して`r_eff`を計算してください。
