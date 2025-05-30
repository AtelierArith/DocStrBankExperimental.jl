```
infer
```

入力から出力タイプを推測します。対応する `AbstractAlgorithm` から `AbstractDiagnostics` を推測します。

# 例

```julia
infer(_rng, diagnostics::Type{AbstractDiagnostics}, algorithm, model, data)
```
