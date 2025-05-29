```julia
sysappscore(s::Santiago.System; α) -> Float64

```

システム適合性スコア（SAS）を計算します。 `α` ∈ [0, 1] は算術平均（α=0）から幾何平均（`α=1`）に徐々に変化します。
