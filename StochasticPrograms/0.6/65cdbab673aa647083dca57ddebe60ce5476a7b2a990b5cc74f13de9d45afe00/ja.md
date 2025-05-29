```
VRP(stochasticprogram::StochasticProgram)
```

**再帰問題の値** (`VRP`) を `stochasticprogram` で計算します。

言い換えれば、確率的プログラムを最適化し、最適値を返します。

まだオプティマイザが設定されていない場合（[`set_optimizer`](@ref) を参照）、`NoOptimizer` エラーがスローされます。

関連情報: [`EVPI`](@ref), [`EWS`](@ref)
