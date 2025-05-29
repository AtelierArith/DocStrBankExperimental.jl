```
contourplot(A; kw...)
```

# 使用法

行列 `A` の等高線プロットを新しいキャンバス上の `x` 軸と `y` 軸に描画します。

`y` 軸はデフォルトで反転されています：

```
Julia matrices (images) │ UnicodePlots
                        │
           axes(A, 2)   │
           o───────→    │   ↑
           │            │   │
axes(A, 1) │            │ y │
           │            │   │
           ↓            │   o───────→
                        │       x
```
