```
energy_total_modified(q_global, equations, cache)
```

原始変数 `q_global` の修正された総エネルギーを `equations` のために返します。この修正された総エネルギーは保存量であり、通常の [`energy_total`](@ref) と比較して追加の項を含むことがあります。例えば、[`SvaerdKalischEquations1D`](@ref) と [`SerreGreenNaghdiEquations1D`](@ref) の場合、非水平方向の寄与をモデル化する速度 $v_x$ の導関数に依存する追加の項が含まれています。`AbstractShallowWaterEquations` でない方程式の場合、修正された総エネルギーは通常の [`energy_total`](@ref) の拡張である必要はなく、物理的エネルギーに関連している必要もありません。しかし、適切な境界条件に対しては依然として保存量であり、解の導関数を含む可能性があります。

`q_global` はすべてのノードでの原始変数のベクトルです。`cache` は、非水平方向の項が存在する場合に `solver` によって使用される SBP 演算子を保持する必要があります。

内部的に、この関数は出力用のベクトルを割り当て、[`DispersiveShallowWater.energy_total_modified!`](@ref) を呼び出します。
