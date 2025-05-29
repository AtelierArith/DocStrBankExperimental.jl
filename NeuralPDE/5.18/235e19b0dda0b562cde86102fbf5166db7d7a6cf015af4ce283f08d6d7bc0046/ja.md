```
neural_adapter(loss, init_params, pde_system, strategy)
```

既に得られた予測の結果を使用してニューラルネットワークをトレーニングします。

## 位置引数

  * `loss`: 損失関数の本体、
  * `init_params`: ニューラルネットワークの初期パラメータ、
  * `pde_system`: PDEはModelingToolkit.jlを使用して定義されます、
  * `strategy`: どのトレーニング戦略が使用されるかを決定します。
