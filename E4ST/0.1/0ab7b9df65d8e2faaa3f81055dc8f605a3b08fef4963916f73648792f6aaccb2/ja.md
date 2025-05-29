```
constrain_pbal!(config, data, model) -> nothing
```

各バスの電力バランス方程式を、各年および各時間においてゼロに等しく制約します。

`config[:line_loss_type]` に応じて、電力バランス方程式は2つの方法で実装できます：

  * `pflow`:  `plgen_bus - plserv_bus + pflow_in_bus * (1 - line_loss_rate) - pflow_out_bus == 0`
  * `plserv`:  `plgen_bus - plserv_bus / (1 - line_loss_rate) - pflow_bus == 0`

ここで：

  * `pgen_bus` はバスで生成される電力です
  * `plserv_bus` はバスで供給/消費される電力です
  * `pflow_bus` はバスから流出するネット電力（正または負）です
  * `pflow_in_bus` はバスに流入する（正の）電力です
  * `pflow_out_bus` はバスから流出する（正の）電力です
