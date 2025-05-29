```
PositivityPreservingLimiterZhangShu(; threshold, variables)
```

完全離散の正定性保持リミッタは

  * Zhang, Shu (2011) 最大原則を満たし、正定性を保持する高次スキームの保存法則に関する調査と新しい展開 [doi: 10.1098/rspa.2011.0153](https://doi.org/10.1098/rspa.2011.0153)

リミッタは、与えられた順序で全てのスカラー `variables` に適用され、関連する `thresholds` を使用して最小限の受け入れ可能な値を決定します。`variables` の順序は重要であり、堅牢性に強い影響を与える可能性があります。
