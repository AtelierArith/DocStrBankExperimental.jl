```
pirls!(m::GeneralizedLinearMixedModel)
```

ペナルティ付き反復加重最小二乗法 (PIRLS) を使用して、ランダム効果の条件付きモードを決定します。

`varyβ` が true の場合、`u` と `β` の両方が PIRLS で最適化されます。それ以外の場合は、`u` のみが最適化され、`β` は固定されます。

`verbose = true` を渡すと、反復の詳細な出力が提供されます。
