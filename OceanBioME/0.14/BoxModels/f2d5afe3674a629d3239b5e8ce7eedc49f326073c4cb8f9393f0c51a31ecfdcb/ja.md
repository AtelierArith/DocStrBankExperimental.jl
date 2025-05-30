```
BoxModel(; biogeochemistry,
           forcing = NamedTuple(),
           timestepper = :RungeKutta3,
           clock = Clock(; time = 0.0),
           prescribed_tracers::PT = NamedTuple())
```

`biogeochemistry`モデルのボックスモデルを構築します。これが構築されたら、`set!(model, X=1.0...)`を使って初期条件を設定できます。

# キーワード引数

  * `biogeochemistry`: (必須) OceanBioMEの生物地球化学モデルで、ほとんどのモデルには`BoxModelGrid`に設定できる`grid`を渡す必要があります
  * `forcing`: 生物地球化学トレーサーを統合するための追加の強制関数のNamedTuple
  * `timestepper`: モデルを統合するためのタイムステッパー
  * `clock`: 時間を追跡するためのOceananigansの時計
  * `prescribed_tracers`: トレーサー名とトレーサー値を指定する関数(`f(t)`)の名前付きタプル
