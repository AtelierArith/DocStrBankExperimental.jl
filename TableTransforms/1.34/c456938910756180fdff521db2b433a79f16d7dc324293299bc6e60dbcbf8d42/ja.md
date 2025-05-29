```
PCA([options])
```

主成分分析。

詳細なオプションの説明については、[`EigenAnalysis`](@ref)を参照してください。

# 例

```julia
PCA(maxdim=2)
PCA(pratio=0.86)
PCA(maxdim=2, pratio=0.86)
```

## 注意事項

  * `PCA()`は`ZScore() → EigenAnalysis(:V)`のショートカットです。
