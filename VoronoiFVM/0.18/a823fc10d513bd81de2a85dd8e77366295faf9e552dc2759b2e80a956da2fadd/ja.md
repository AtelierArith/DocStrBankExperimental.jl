```
timesteps!(control,Δt; grow=1.0)
```

制御データを修正して、時間ステップを幾何級数に固定します。すなわち、Δt*new=Δt*old*grow です。
