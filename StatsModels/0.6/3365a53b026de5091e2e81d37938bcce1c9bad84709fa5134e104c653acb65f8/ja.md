```
DummyCoding([base[, levels]])
DummyCoding(; base=nothing, levels=nothing)
```

ダミーコーディングは、各非ベースレベルに対して1つのインジケーター列（1または0）を生成します。

`levels`が省略されるか`nothing`の場合、`ContrastsMatrix`を構築する際にデータに対して`levels`関数を呼び出すことで決定されます。`base`が省略されるか`nothing`の場合、最初のレベルがベースとして使用されます。

列は非ゼロ平均を持ち、切片列（および相互作用のための低次列）と共線的ですが、お互いには直交しています。回帰モデルでは、ダミーコーディングはベースレベルの従属変数の平均となる切片をもたらします。

「トリートメントコーディング」または「ワンホットエンコーディング」としても知られています。

# 例

```julia
julia> StatsModels.ContrastsMatrix(DummyCoding(), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 0.0  0.0  0.0
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
