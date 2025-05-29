```
PeriodicCallback(affect, interval; [offset=0.0, initialize, finalize])
```

`affect`を[`prepropagate!`](@ref)フックで毎`interval`シミュレーション時間単位ごとに実行するコールバックを返します。**`offset + interval`から開始します**。`initialize`および`finalize`関数は、コールバックが最初に実行されるときと、シミュレーションが正常に終了したときにそれぞれ呼び出されます。
