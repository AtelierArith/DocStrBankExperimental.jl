```
DRS([options])
```

次元削減スフィアリング。

利用可能なオプションの詳細な説明については、[`EigenAnalysis`](@ref)を参照してください。

# 例

```julia
DRS(maxdim=3)
DRS(pratio=0.87)
DRS(maxdim=3, pratio=0.87)
```

## 注意事項

  * `DRS()`は`ZScore() → EigenAnalysis(:VD)`のショートカットです。
