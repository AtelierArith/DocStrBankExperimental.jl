```
Sv(ping::EK60Ping;
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

指定された`ping`に対する体積後方散乱強度（MVBS）の`Vector`を返します（dB re 1 m-1）。

この関数は、指定された場合、pingの設定を上書きするオプションの引数をいくつか受け入れます。これにより、外部キャリブレーションが容易になります。
