```
LJRefIdeal <: IdealModel
LJRef(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - 粒子サイズ [Å]
  * `epsilon`: 単一パラメータ (`Float64`) - 分散エネルギー [`K`]
  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`

## 説明

レナード-ジョーンズ参照状態方程式。理想的な部分。0.5 < T/Tc < 7 および p/pc = 500 までの圧力で有効です。

```
τᵢ = 1.32ϵᵢ/T
δᵢ = n(Nₐσᵢ^3)/0.31V
a⁰ᵢ(δ,τ) = log(δᵢ) + 1.5log(τᵢ) - 1.515151515τᵢ + 6.262265814
a⁰(δ,τ,z) = ∑xᵢ(a⁰ᵢ + log(xᵢ))

```

`LJRefIdeal` は `LJRef` モデルのラッパーとして機能し、`LJRef(model::LJRefIdeal)` でアクセスできます。

!!! 警告 "複数成分の警告"     元のモデルは1つの成分のみを考慮して作成されました。複数成分をサポートするために、VDW 1-fluid 混合則（上記参照）が実装されていますが、テストは行われていません。

## 参考文献

1. Thol, M., Rutkai, G., Köster, A., Lustig, R., Span, R., & Vrabec, J. (2016). レナード-ジョーンズ流体の状態方程式。物理化学参考データジャーナル, 45(2), 023101. [doi:10.1063/1.4945000](https://doi.org/10.1063/1.4945000)
