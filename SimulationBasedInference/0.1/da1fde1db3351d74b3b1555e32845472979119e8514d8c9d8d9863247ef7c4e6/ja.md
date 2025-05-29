```
get_transformed_ensemble(sol::SimulatorInferenceSolution{<:EnsembleInferenceAlgorithm}, iter::Int=-1)
```

与えられたソリューションオブジェクトから変換されたアンサンブルを取得します。反復アルゴリズムの場合、オプションの引数 `iter` を指定することができ、指定された反復でアンサンブルを取得します。
