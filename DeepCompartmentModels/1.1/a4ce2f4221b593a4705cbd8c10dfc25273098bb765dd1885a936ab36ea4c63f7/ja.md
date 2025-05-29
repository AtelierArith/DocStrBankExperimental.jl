```
LowDimensionalNeuralODE(ann, node; kwargs...)
```

低次元Neural-ODEベースのモデルを構築するための便利な関数。このシンプルな実装は、次のようにモデルを学習します：

```
du/dt = node.u(u) + I * node.t(t)
```

ここで、モデルは前の状態uと現在の時間点tに基づいてシステムの動力学を学習します。詳細については[bram2023]を参照してください。

# 引数:

  * `u`: 入力として`u`を取るNeuralODE。
  * `t`: 入力として`t`を取るNeuralODE。
  * `kwargs`: NeuralODEコンストラクタに渡されるキーワード引数。

[bram2023] Bräm, Dominic Stefan, et al. "Low-dimensional neural ODEs and their application in pharmacokinetics." Journal of Pharmacokinetics and Pharmacodynamics (2023): 1-18.
