```julia
clock_gettime(id) -> ts
```

は、指定された時計 `id` の時間を返します。結果は `IPC.TimeSpec` のインスタンスです。時計識別子 `id` は次のいずれかです：

  * `CLOCK_REALTIME`: 実際の（すなわち、壁時計）時間を測定するシステム全体の時計。この時計は、システム管理者が手動で時計を変更した場合など、システム時間の不連続なジャンプの影響を受け、`adjtime` や NTP によって行われる増分調整の影響も受けます。
  * `CLOCK_MONOTONIC`: 設定できない時計で、特定の開始点からの単調時間を表します。この時計は、システム時間の不連続なジャンプの影響を受けません。

さらに [`clock_getres`](@ref)、[`clock_settime`](@ref)、[`gettimeofday`](@ref)、[`nanosleep`](@ref)、[`IPC.TimeSpec`](@ref) および [`IPC.TimeVal`](@ref) も参照してください。
