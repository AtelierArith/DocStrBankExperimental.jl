```
compress_timesteps(timesteps, forces = nothing; max_step = Inf)
```

タイムステップと力のセットを圧縮し、同じ間隔をカバーし、力が正確に同じ時間で変化する最大のステップにしますが、`max_step`の最大サイズに制限されます。
