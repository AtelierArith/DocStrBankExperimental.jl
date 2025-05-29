```
ODEFunction(problem)
```

[`SkeelBerzins.assemble!`](@ref) 関数で導出された空間離散化から [ODEFunction](https://docs.sciml.ai/DiffEqDocs/stable/types/ode_types/#SciMLBase.ODEFunction) を生成します。質量行列が単位行列と異なる場合は [質量行列 ODE](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/dae_example/) として表現され、そうでない場合は単純な [ODEの系](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/advanced_ode_example/#stiff) として表現され、スパースパターンに関して問題を定義します。

入力引数:

  * `problem`: [`SkeelBerzins.ProblemDefinition`](@ref) 型の構造体。
