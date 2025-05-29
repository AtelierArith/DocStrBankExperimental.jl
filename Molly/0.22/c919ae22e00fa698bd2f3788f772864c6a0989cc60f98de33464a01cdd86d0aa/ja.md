```
MonteCarloLogger()
MonteCarloLogger(T)
```

モンテカルロシミュレーションにおける受け入れを記録するロガーです。

記録される量には、新しい選択の数（`n_select`）、成功した受け入れの数（`n_accept`）、状態のボルツマン因子の引数である$\frac{E}{k_B T}$の値を格納する`energy_rates`という名前の配列、そして記録されたステップで新しい状態が受け入れられたかどうかを格納する`BitVector`という名前の`state_changed`が含まれます。
