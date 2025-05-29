```
SolidHfusModel <: EoSModel

SolidHfus(components;
userlocations = String[],
verbose::Bool=false)
```

## パラメータ

  * `Hfus`: 単一パラメータ (`Float64`) - 1バールでの融解エンタルピー `[J/mol]`
  * `Tm`: 単一パラメータ (`Float64`) - 融点 `[K]`
  * `CpSL`: 単一パラメータ (`Float64`) (オプション) - 固体-液体相転移の比熱容量 `[J/mol/K]`

## 説明

固体相における過剰化学ポテンシャルの近似 (`CpSL` はデフォルトでは必要ありません):

```
ln(xᵢγᵢ) = Hfusᵢ*T*(1/Tmᵢ-1/T)-CpSLᵢ/R̄*(Tmᵢ/T-1-log(Tmᵢ/T))
```
