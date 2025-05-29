```
SolidKsModel <: EoSModel

SolidKs(components;
userlocations = String[],
verbose::Bool=false)
```

## パラメータ

  * `Hfus`: 単一パラメータ (`Float64`) - 1バールでの融解エンタルピー `[J/mol]`
  * `Tm`: 単一パラメータ (`Float64`) - 融点 `[K]`
  * `CpSL`: 単一パラメータ (`Float64`) - 固体-液体相転移の比熱容量 `[J/mol/K]`

## 説明

エンタルピーとギブズ生成エネルギーを使用して、固体相における過剰化学ポテンシャルの近似：

```
ln(xᵢγᵢ) = -Gformᵢ*T/Trefᵢ - Hformᵢ*(1 - T/Trefᵢ)
```
