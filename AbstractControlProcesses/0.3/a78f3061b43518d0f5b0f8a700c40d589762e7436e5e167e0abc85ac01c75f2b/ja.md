```
last_time = periodic_wait(P::AbstractProcess, last_time, dt)
```

次の周期の開始時に実行を続ける必要があります。つまり、`last_time`から`dt`秒が経過したときです。

`PhysicalProcess`の場合、これはデフォルトの実装があり、`last_time + dt`までスリープします。これは`Libc.systemsleep`を使用しています。これはJuliaの標準の`sleep`を使用するよりも正確ですが、実行中のJuliaスレッド全体をブロックするため、場合によっては実行に影響を与える可能性があります。

`SimulatedProcess`の場合、リアルタイムでバックグラウンドプロセスで実行されるか、物理プロセスと同様に実装されるべきです。または、フルシミュレーション速度で実行される場合、`periodic_wait`が呼び出されたときに環境が`dt`時間に対応するステップをシミュレートする必要があります。

`last_time`を正しい値に初期化する良い方法は、`last_time = periodic_wait(P, 0.0, 0.0)`を呼び出すことです。
