```
select_snapshots(s::SteadySnapshots,prange) -> SnapshotsAtIndices
select_snapshots(s::TransientSnapshots,trange,prange) -> TransientSnapshotsAtIndices
```

Restricts the parametric range of `s` to the indices `prange` steady cases, to the indices `trange` and `prange` in transient cases, while leaving the spatial entries intact. The restriction operation is lazy.
