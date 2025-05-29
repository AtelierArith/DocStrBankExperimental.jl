```
HelmertCoding([base[, levels]])
HelmertCoding(; base=nothing, levels=nothing)
```

ヘルマートコーディングは、各レベルを下位レベルの平均からの差としてコード化します。

`levels` が省略されるか `nothing` の場合、`Contrastsmatrix` を構築する際に `levels` 関数を呼び出すことでデータから決定されます。`base` が省略されるか `nothing` の場合、最初のレベルがベースとして使用されます。非ベースレベルごとに、ヘルマートコーディングは、下位の n レベルごとに -1、該当レベルに n、上位に 0 の列を生成します。

すべてのレベルが同じ頻度である場合、ヘルマートコーディングは平均中心（平均 0）で直交する列を生成します。

# 例

```julia
julia> StatsModels.ContrastsMatrix(HelmertCoding(), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 -1.0  -1.0  -1.0
  1.0  -1.0  -1.0
  0.0   2.0  -1.0
  0.0   0.0   3.0
```
