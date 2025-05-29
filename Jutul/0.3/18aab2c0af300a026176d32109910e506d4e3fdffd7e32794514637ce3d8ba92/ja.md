```
model_accumulation!(acc, sim::HelperSimulator, x, dt = 1.0;
    forces = setup_forces(sim.model),
    update_secondary = true,
    kwarg...
)
```

ベクトル acc に蓄積項を計算します。
