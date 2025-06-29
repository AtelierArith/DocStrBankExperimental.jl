```
Rprop(η = 1f-3, ℓ = (5f-1, 1.2f0), Γ = (1f-6, 50f0))
```

[Rprop](https://ieeexplore.ieee.org/document/298623)アルゴリズムを使用したオプティマイザ。勾配の符号のみに依存するフルバッチ学習アルゴリズムです。

# パラメータ

  * 学習率（`η`）：重みを更新する前に勾配が割引かれる量。
  * スケーリングファクター（`ℓ::Tuple`）：乗算的な増加および減少の因子。
  * ステップサイズ（`Γ::Tuple`）：許可される最小および最大のステップサイズ。
