Simulationは`run!(::Simulation)`と一緒に使用されるコンテナ構造体です。以下を含みます。

  * `prognostic_variables::SpeedyWeather.PrognosticVariables`: モデルの現在の状態を定義します
  * `diagnostic_variables::SpeedyWeather.DiagnosticVariables`: 傾向とそれを計算するための補助配列を含みます
  * `model::SpeedyWeather.AbstractModel`: 実行時に定数のすべてのパラメータ
