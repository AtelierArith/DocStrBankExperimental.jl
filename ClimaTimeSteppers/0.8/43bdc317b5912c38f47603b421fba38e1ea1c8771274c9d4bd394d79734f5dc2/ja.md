```
AbstractAlgorithmConstraint
```

ODEを解くためのアルゴリズムが実行できる操作を制約するメカニズムです。

例えば、制約のないアルゴリズムは、傾向の線形結合を取ることによってルンゲ・クッタのステージを計算するかもしれません。すなわち、`dt * tendency(state)`の形の量を加算します。一方で、「強安定性保存」アルゴリズムは「増加した状態」の線形結合のみを取ることができます。すなわち、`state + dt * coefficient * tendency(state)`の形の量のみを加算します。
