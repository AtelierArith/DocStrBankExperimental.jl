# 拡張ヘルプ

```
constraints_list(am::AbstractAffineMap)
```

### 注意事項

基になる集合 `X` が多面体であると仮定します。すなわち、`constraints_list(X)` メソッドを提供します。

### アルゴリズム

この実装は、`constraints_list` メソッドを使用して、遅延 [`LinearMap`](@ref) の翻訳の制約リストを計算します。
