```
Kp, Ti, Td = convert_pidparams_to_parallel(param_p, param_i, param_d, form)
```

パラメータを形式 `form` から `:parallel` 形式に変換します。

`form` は以下のいずれかを選択できます。

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$
