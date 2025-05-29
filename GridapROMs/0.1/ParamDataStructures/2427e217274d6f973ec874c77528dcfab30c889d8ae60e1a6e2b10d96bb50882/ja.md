```
select_snapshots(s::SteadySnapshots,prange) -> SnapshotsAtIndices
select_snapshots(s::TransientSnapshots,trange,prange) -> TransientSnapshotsAtIndices
```

`s`のパラメトリック範囲を、定常ケースのインデックス`prange`に、過渡ケースのインデックス`trange`と`prange`に制限し、空間エントリはそのままにします。制限操作は遅延です。
