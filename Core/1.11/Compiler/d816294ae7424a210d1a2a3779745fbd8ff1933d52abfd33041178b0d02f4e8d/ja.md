```
finish(interp::AbstractInterpreter, opt::OptimizationState,
       ir::IRCode, caller::InferenceResult)
```

Juliaレベルの最適化から得られた情報を後処理して、後で使用します。特に、この関数は最適化されたコードのインライン化可能性を決定します。
