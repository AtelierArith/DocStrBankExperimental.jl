```
Clock(; time, last_Δt=Inf, last_stage_Δt=Inf, iteration=0, stage=1)
```

`Clock`オブジェクトを返します。デフォルトでは、`Clock`はゼロ番目の`iteration`と最初の時間ステップ`stage`に初期化され、`last_Δt=last_stage_Δt=Inf`となります。
