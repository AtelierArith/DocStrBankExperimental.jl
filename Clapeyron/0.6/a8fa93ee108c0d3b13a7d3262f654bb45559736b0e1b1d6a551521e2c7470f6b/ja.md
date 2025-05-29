```
EOS_LNG::MultiFluid

EOS_LNG(components::Vector{String};
Rgas = 8.314472,
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

なし

## 説明

EOS-LNG: 液化天然ガスの熱力学的性質を計算するための基本的な状態方程式。21種類の化合物（`Clapeyron.GERG2008_names`）に対して有効です。このEoSは、メタン + n-ブタン、メタン + イソブタン、メタン + n-ペンタン、メタン + イソペンタンの新しい二元特有のパラメータを持っています。

それは[`GERG2008`](@ref)と同じ機能形式を使用しています。

## 参考文献

1. Thol, M., Richter, M., May, E. F., Lemmon, E. W., & Span, R. (2019). EOS-LNG: A fundamental equation of state for the calculation of thermodynamic properties of liquefied natural gases. Journal of Physical and Chemical Reference Data, 48(3), 033102. [doi:10.1063/1.5093800](https://doi.org/10.1063/1.5093800)
2. Kunz, O., & Wagner, W. (2012). The GERG-2008 wide-range equation of state for natural gases and other mixtures: An expansion of GERG-2004. Journal of Chemical and Engineering Data, 57(11), 3032–3091. [doi:10.1021/je300655b](https://doi.org/10.1021/je300655b)
