```julia
finalize!(
    simulation::SpeedyWeather.AbstractSimulation
) -> Any

```

`simulation`を最終化します。進行メーターを終了し、変数のスケールを解除し、出力を最終化し、再起動ファイルを書き込み、コールバックを最終化します。
