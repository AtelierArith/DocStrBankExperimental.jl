```
generate_trials!(sim_inst::SimulationInstance{T}, samples::Int; filename::Union{String, Nothing}=nothing)
```

指定された `SimulationInstance` のために定義された `samplesize` を使用してトライアルを生成します。この関数は、すべてのシナリオで使用されるデータを事前に生成するためにシミュレーションを実行する前に呼び出してください。また、ファイル名が指定されている場合は入力を保存します。
