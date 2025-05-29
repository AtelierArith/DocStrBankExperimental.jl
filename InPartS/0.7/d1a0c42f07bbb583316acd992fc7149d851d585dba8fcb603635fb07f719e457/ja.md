```
readsnap(snapgroup, sim::Simulation; [warn = IOWARN[]]) → particles, time, step, next_id, rng[,...]
```

`snapgroup`からスナップショットを読み込み、`sim`からの追加情報を使用します。シミュレーションに適用できる状態情報のタプルを返します [`setstate`]((@ref)
