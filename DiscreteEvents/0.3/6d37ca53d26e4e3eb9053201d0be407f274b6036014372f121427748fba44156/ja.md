```
Clock(Δt::T=0.01; t0::U=0, unit::FreeUnits=NoUnits) where {T<:Number,U<:Number}
```

新しい仮想時計を作成します。

# 引数

  * `Δt::T=0.01`: サンプリングのための時間増分。Δtは後で`sample_time!`で設定できます。
  * `t0::U=0`: シミュレーションの開始時間
  * `unit::FreeUnits=NoUnits`: 時計の時間単位。単位は、例えば`unit=minute`と明示的に設定するか、Δtを時間として与えるか、または`t0`を時間に設定することで暗黙的に設定できます。例: `t0=60s`。

作成された時計のidは1（マスター）です。
