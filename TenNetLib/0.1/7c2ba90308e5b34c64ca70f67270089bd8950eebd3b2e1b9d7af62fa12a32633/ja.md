```
function updateH!(engine::TDVPEngine, H::T;
                  recalcEnv::Bool = true) where T <: Union{MPO, Vector{MPO}, CouplingModel}
```

エンジン `engine::TDVPEngine` のハミルトニアン `H` を更新します。`recalcEnv = false` の場合、以前の環境を再利用します。`recalcEnv = false` は、`TDVPEngine` が単一の `MPO` から作成されたときのみ定義されます。
