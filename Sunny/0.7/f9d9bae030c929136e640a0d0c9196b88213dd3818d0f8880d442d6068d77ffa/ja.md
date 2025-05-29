```
repeat_periodically(sys::System, counts::NTuple{3, Int})
```

指定された `counts` に従って、各システム軸に沿って指定された回数だけ繰り返された `sys` と同一の [`System`](@ref) を作成します。これは、より一般的な [`reshape_supercell`](@ref) の特別なケースです。

また、周期的なコピー間でスピンを回転させる [`repeat_periodically_as_spiral`](@ref) も参照してください。
