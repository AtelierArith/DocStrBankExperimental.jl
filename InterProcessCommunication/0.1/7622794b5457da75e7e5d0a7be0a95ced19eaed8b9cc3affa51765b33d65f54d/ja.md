```julia
clock_getres(id) -> ts
```

は、指定されたクロック `id` の解像度（精度）を返します。結果は `IPC.TimeSpec` のインスタンスです。クロック識別子 `id` は `CLOCK_REALTIME` または `CLOCK_MONOTONIC` であることができます（[`clock_gettime`](@ref) で説明されています）。

他にも [`clock_gettime`](@ref)、[`clock_settime`](@ref)、[`gettimeofday`](@ref)、[`nanosleep`](@ref)、[`IPC.TimeSpec`](@ref) および [`IPC.TimeVal`](@ref) を参照してください。
