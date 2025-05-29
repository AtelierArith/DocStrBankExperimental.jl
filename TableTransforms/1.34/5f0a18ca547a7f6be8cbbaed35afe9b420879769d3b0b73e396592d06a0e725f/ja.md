```
SDS([options])
```

標準化データスフィアリング。

利用可能なオプションの詳細な説明については、[`EigenAnalysis`](@ref)を参照してください。

# 例

```julia
SDS()
SDS(maxdim=4)
SDS(pratio=0.88)
SDS(maxdim=4, pratio=0.88)
```

## 注意事項

  * `SDS()`は`ZScore() → EigenAnalysis(:VDV)`のショートカットです。

```
