```
season_run!(cropfield::AquaCropField)
```

現在のシーズンのすべての日に対して`cropfield`を更新します。

`NormalFileRun`または`TomlFileRun`を使用してデータをアップロードし、複数のシーズンを指定した場合、最初のシーズンのみが実行されます。

`NoFileRun`を使用してデータをアップロードした場合、`Simulation_DayNr1`から`Simulation_DayNrN`までのシミュレーションが実行されます。
