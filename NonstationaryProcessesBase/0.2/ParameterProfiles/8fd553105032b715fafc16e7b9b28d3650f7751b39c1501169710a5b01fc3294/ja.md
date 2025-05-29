```
unitStep(threshold::Real=0.0, baseline::Real=0.0, stepHeight::Real=1.0, stepOpt::Real=1.0)
```

閾値'threshold'で'baseline'から'stepHeight'のサイズのステップを経る'x'の定数関数を構築します。'stepOpt'は0での値を設定します。非連続型が返され、通常の関数のように呼び出すことができますが、不連続性があるx値も含まれています。

# 例

```julia-repl
julia> D = unitStep();
D([-1, 0, 1])
```
