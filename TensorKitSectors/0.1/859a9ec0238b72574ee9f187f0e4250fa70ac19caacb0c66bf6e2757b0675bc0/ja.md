```
struct IsingAnyon <: Sector
IsingAnyon(s::Symbol)
```

イジングモジュラー融合カテゴリのアニオンを表します。これは、トリビアルセクター `IsingAnyon(:I)` と非トリビアルセクター `IsingAnyon(:σ)` および `IsingAnyon(:ψ)` に対応する3つの値を取ることができます。融合則は $ψ ⊗ ψ = 1$、$σ ⊗ ψ = σ$、および $σ ⊗ σ = 1 ⊕ ψ$ です。

## フィールド

  * `s::Symbol`: 表 represented アニオンのラベルで、`:I`、`:σ`、または `:ψ` になります。
