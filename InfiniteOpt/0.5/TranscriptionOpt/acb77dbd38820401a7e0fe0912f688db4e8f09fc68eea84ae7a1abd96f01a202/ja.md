```
transcription_expression(trans_model::JuMP.Model, expr, support::Vector{Float64})
```

`expr`が`InfiniteModel`からのものである場合、`support`で定義された`trans_model`に利用可能な変数マッピングに従って、その転写されたバージョンを形成します。これは、すべての変数と測定が転写された後（例えば、[`transcribe_finite_variables!`](@ref)を介して）にのみ使用するべきです。
