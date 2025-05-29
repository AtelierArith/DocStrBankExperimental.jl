```
is_reachable(gate::AbstractMatrix{<:Number}, system::AbstractQuantumSystem; kwargs...)
```

与えられた `system` を使用して `gate` が到達可能かどうかを確認します。

# キーワード引数

  * `use_drift::Bool=true`: 演算子にドリフトハミルトニアンを含める
  * `kwargs...`: `is_reachable` のためのキーワード引数
