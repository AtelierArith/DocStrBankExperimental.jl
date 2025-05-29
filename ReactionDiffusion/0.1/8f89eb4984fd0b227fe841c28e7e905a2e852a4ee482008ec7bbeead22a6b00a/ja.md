```
get_params(model, turing_param)
```

与えられた `model` と *単一* のパターン形成パラメータセット `turing_param` に対して、この関数は対応する `model_parameters` 変数を作成します。これにより、デフォルトで `model_parameters` フィールドが設定されます：

  * `domain_size`: 計算されたパターン波長の3倍に選ばれます。すなわち、`3*turing_param.wavelength`
  * `initial_condition`: 計算された定常状態の値に選ばれます。すなわち、 `turing_param.steady_state_values`
  * `initial_noise = 0.01`: 定常状態の値に追加されるノイズの大きさ（正規分布に従うランダム数）で、初期条件を定義します。
