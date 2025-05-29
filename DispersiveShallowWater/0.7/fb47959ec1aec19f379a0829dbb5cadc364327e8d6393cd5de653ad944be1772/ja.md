```
DispersiveShallowWater
```

**DispersiveShallowWater.jl** は、分散浅水モデルのための構造を保持する数値手法を実装したJuliaパッケージです。これは、いくつかの分散浅水モデルに対して、証明可能な保存的、エントロピー保存、そして良好にバランスの取れた数値スキームを提供します。

半離散化は、[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl) に実装された部分和（SBP）演算子に基づいています。完全に離散化されたスキームを得るために、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) の時間積分法を使用して、得られた常微分方程式を解きます。完全に離散化されたエントロピー保存法は、DispersiveShallowWater.jlが提供する緩和法を使用することで得られます。

さらに詳しくは: [DispersiveShallowWater.jl](https://github.com/NumericalMathematics/DispersiveShallowWater.jl)
