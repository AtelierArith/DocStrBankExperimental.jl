```julia
initialize!(
    simulation::SpeedyWeather.AbstractSimulation;
    period,
    steps,
    output
) -> Any

```

`simulation`を初期化します。変数をスケーリングし、出力を初期化し、初期条件を保存し、進捗メーターのフィードバック、コールバックを初期化し、リープフロッギングスキームをスピンアップするために最初の2つの初期時間ステップを実行します。
