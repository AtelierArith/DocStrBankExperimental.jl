```
latticize!(kpi::KPathInterpolant{D})
```

補間された **k**-パス `kpi` を直交基底から格子基底に（原始的な）逆格子ベクトル `basis(kpi)` を用いてインプレースで変換します。
