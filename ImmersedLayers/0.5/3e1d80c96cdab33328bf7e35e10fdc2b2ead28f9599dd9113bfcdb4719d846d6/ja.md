```
surfaces(u::ConstrainedSystems.ArrayPartition,sys::ILMSystem,t) -> BodyList
```

解決ベクトル `u` における表面のリスト（`BodyList` として）を返します。表面が静止している場合、これは単に `sys` からそれらを返し、時間引数は無視されます。
