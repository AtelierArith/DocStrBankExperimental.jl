ZygoteAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing,true,nothing}

Zygote.jlのソースからソースへのADを使用して、微分方程式ソルバーに直接適用した離散的隣接感度分析の実装です。

## コンストラクタ

```julia
ZygoteAdjoint()
```

## SciMLProblem サポート

現在、ほぼすべてのソルバーで失敗します。
