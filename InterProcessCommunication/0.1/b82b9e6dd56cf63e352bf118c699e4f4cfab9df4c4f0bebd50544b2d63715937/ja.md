```julia
nanosleep(t) -> rem
```

`sleeps`は、ナノ秒精度で`t`秒間スリープし、残りの時間（中断があった場合）を`IPC.TimeSpec`のインスタンスとして返します。引数は（小数）秒数、または`IPC.TimeSpec`または`IPC.TimeVal`のインスタンスであることができます。

Juliaが提供する`sleep`メソッドはミリ秒精度のみです。

関連情報としては、[`gettimeofday`](@ref)、[`IPC.TimeSpec`](@ref)、および[`IPC.TimeVal`](@ref)があります。
