```
define_line_amps_pu(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

線のアンペアを$|(V_i - V_j) / Z|$として推定します。ここで、近似を使用します：

$$
|V_i - V_j| \approx r_{ij} P_{ij} + x_{ij} Q_{ij}
$$

式は`model.obj_dict`にキー`:amps_pu`で保存されます。
