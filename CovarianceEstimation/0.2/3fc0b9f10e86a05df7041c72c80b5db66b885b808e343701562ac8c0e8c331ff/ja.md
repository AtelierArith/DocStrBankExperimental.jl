```
WoodburyEstimator(loss::LossFunction, rank::Integer;
                  σ²::Union{Real,Nothing}=nothing, corrected::Bool=false)
```

共分散行列は「スパイク」共分散モデルを使用して推定されるべきであることを指定します。

```
Σ = σ²I + U * Λ * U'
```

`loss` は [`NormLossCov`](@ref) または [`StatLossCov`](@ref) オブジェクトのいずれかであり、推定された共分散が最適となる損失関数を指定します。`rank` はモデルに保持する最大の固有値 `Λ` の数です。オプションで、`σ²` を直接指定することもできますし、データ行列から推定することもできます（`σ²=nothing`）。バイアスのない分散推定量を使用するには、`corrected=true` に設定します。
