`EnergyModelsInvestments`のメインモジュール。

このモジュールは、[EnergyModelsX](https://github.com/EnergyModelsX)システム最適化モデルの投資分析を実行する機能を実装しています。

`EnergyModelsInvestments`はスタンドアロンモデルとして使用することはできません。代わりに、既存のモデルを拡張し、投資決定の組み込みを簡素化します。特定の関数が宣言されている限り、任意のJuMPモデルで使用できます。1つの例は[`EnergyModelsBase`](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/)によって示されています。
