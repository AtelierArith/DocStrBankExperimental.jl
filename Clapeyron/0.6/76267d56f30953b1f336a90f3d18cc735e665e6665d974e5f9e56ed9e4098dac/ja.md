```
CPLNGEstIdeal <: ReidIdealModel

CPLNGEstIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `coeffs`: 単一パラメータ (`NTuple{5,Float64}`) - 多項式係数

## 説明

分子量を入力として使用して、Reid多項式の推定：

```
Cpᵢ(T) = aᵢ  + bᵢT + cᵢT^2 + dᵢT^3
Cp(T) = ∑Cpᵢxᵢ
a = -10.9602   * γ₀ + 25.9033
b = 2.1517e-1  * γ₀ - 6.8687e-2 
c = -1.3337e-4 * γ₀ + 8.6387e-5
d = 3.1474e-8  * γ₀ -2.8396e-8
γ₀ = Mw/Mw(air)
```

## モデル構築の例

```
# デフォルトデータベースを使用
idealmodel = CPLNGEstIdeal("water") #単一入力
idealmodel = CPLNGEstIdeal(["water","ethanol"]) #複数成分

# ユーザー提供のパラメータを使用

# ファイルまたはフォルダを渡す
idealmodel = CPLNGEstIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","mw.csv"])

# パラメータを直接渡す
idealmodel = CPLNGEstIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
```

## 参考文献

1. Kareem, L. A., Iwalewa, T. M., & Omeke, J. E. (2014). Isobaric specific heat capacity of natural gas as a function of specific gravity, pressure and temperature. Journal of Natural Gas Science and Engineering, 19, 74–83. [doi:10.1016/j.jngse.2014.04.011]("http://doi.org/10.1016/j.jngse.2014.04.011")
