```julia
clock_settime(id, ts)
```

指定された時計 `id` の時間を `ts` に設定します。引数 `ts` は `IPC.TimeSpec` のインスタンスまたは秒数であることができます。時計識別子 `id` は `CLOCK_REALTIME` または `CLOCK_MONOTONIC` （[`clock_gettime`](@ref)で説明されています）です。

他にも [`clock_getres`](@ref)、[`clock_gettime`](@ref)、[`gettimeofday`](@ref)、[`nanosleep`](@ref)、[`IPC.TimeSpec`](@ref) および [`IPC.TimeVal`](@ref) を参照してください。
