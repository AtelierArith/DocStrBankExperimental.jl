```
Sv(pings::Vector{EK60Ping};
    frequency=nothing,
    gain=nothing,
    equivalentbeamangle=nothing,
    soundvelocity=nothing,
    absorptioncoefficient=nothing,
    transmitpower=nothing,
    pulselength=nothing,
    sacorrection=nothing,
    rangecorrectionoffset=2)
```

指定された連続した `pings` のための体積後方散乱強度（dB re 1 m-1）の `Array` を返します。

この関数は、指定された場合、pings 自身の設定を上書きするオプションの引数をいくつか受け入れます。これにより、外部キャリブレーションが容易になります。
