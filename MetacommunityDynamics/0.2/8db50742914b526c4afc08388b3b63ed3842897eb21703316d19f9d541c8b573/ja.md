```
BevertonHolt{S} <: Model{Population,Biomass,S,Discrete}
```

[Beverton-Holtモデル](https://en.wikipedia.org/wiki/Beverton%E2%80%93Holt_model)は、離散時間の決定論的な個体群動態モデルです。これは、ロジスティックモデルの離散時間版として一般的に解釈されます。

これは次のように表されます。

$$
N_{t+1} =\frac{R_0 M}{N_t + M}N_t
$$

ここで、$K = (R\_0 - 1)M$は収容力です。
