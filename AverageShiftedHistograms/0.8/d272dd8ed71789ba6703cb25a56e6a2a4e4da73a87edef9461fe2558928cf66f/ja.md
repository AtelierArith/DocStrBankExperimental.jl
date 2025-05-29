```
ash!(o::Ash; kw...)
ash!(o::Ash, newdata; kw...)
ash!(o::Ash, newdata, weight::AbstractWeights; kw...)
```

新しいデータ、新しい重み、スムージングパラメータ（キーワード `m`）、またはカーネル（キーワード `kernel`）を使用してAsh推定を更新します:
