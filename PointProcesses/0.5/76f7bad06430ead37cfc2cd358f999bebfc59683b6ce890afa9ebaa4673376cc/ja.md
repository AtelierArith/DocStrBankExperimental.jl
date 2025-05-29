```
integrated_ground_intensity(pp, h, a, b)
```

時間的点過程 `pp` に対して、区間 `[a, b)` の履歴 `h` に適用される統合された地面の強度（または補償器） `Λ(t|h)` を計算します：

```
Λ(h) = ∫ λg(t|h) dt
```
