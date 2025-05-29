```
EOS_LNG::MultiFluid

EOS_LNG(components::Vector{String};
Rgas = R̄,
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

なし

## 説明

EOS-LNG: 液化天然ガスの熱力学的特性を計算するための基本的な状態方程式。21の化合物（`Clapeyron.GERG2008_names`）に対して有効です。このEoSは、メタン + n-ブタン、メタン + イソブタン、メタン + n-ペンタン、メタン + イソペンタンのための新しい二元特有のパラメータを持っています。

それは[`GERG2008`](@ref)と同じ関数形式を使用しています。

## 参考文献

EOS-CG: CCS混合物の熱力学的特性を計算するための混合モデル

それは[`GERG2008`](@ref)と同じ関数形式を使用しています。

## 参考文献

1. Neumann, T., Herrig, S., Bell, I. H., Beckmüller, R., Lemmon, E. W., Thol, M., & Span, R. (2023). EOS-CG-2021: A mixture model for the calculation of thermodynamic properties of CCS mixtures. International Journal of Thermophysics, 44(12). [doi:10.1007/s10765-023-03263-6](https://doi.org/10.1007/s10765-023-03263-6)
