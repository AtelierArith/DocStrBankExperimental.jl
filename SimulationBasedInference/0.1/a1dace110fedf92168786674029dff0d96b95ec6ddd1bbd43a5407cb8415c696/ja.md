```
get_ensemble(sol::SimulatorInferenceSolution{<:EnsembleInferenceAlgorithm}, iter::Int=-1)
```

与えられたソリューションオブジェクトからアンサンブルの状態を取得します。反復アルゴリズムの場合、オプションの引数 `iter` を指定することができ、指定された反復でアンサンブルを取得します。
