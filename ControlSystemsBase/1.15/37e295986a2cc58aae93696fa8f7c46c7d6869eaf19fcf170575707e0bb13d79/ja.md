```
convert_pidparams_from_to(kp, ki, kd, from::Symbol, to::Symbol)
```

PIDパラメータを`from`形式から`to`形式に変換します。

`from`と`to`形式は以下のいずれかを選択できます。

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$
