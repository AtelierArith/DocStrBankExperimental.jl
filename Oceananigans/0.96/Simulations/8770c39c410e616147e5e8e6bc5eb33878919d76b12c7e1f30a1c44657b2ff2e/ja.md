```
Callback(func, schedule=IterationInterval(1);
         parameters=nothing, callsite=TimeStepCallsite())
```

`func`を`callsite`で`schedule`に従って実行する`Callback`を返します。オプションの`parameters`があります。デフォルトでは、`schedule = IterationInterval(1)`および`callsite = TimeStepCallsite()`です。

`parameters`が`nothing`の場合、`func(sim::Simulation)`が呼び出されます。それ以外の場合、`func`は`func(sim::Simulation, parameters)`を介して呼び出されます。

`callsite`は`Callback`が実行される場所を決定します。`callsite`の可能な値は次のとおりです。

  * `TimeStepCallsite()`: 時間ステップの後。
  * `TendencyCallsite()`: 傾向が計算された後、しかし時間ステップを取る前（傾向計算を修正するのに便利）。
  * `UpdateStateCallsite()`: `update_state!`内で、補助変数が計算された後（マルチステージ時間ステッパーの場合、`update_state!`は時間ステップごとに複数回呼び出されることがあります）。
