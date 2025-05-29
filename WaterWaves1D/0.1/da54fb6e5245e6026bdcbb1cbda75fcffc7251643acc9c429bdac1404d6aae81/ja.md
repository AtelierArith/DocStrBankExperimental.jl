```
Problem( model, initial, param ; solver, label)
```

初期値問題を構築し、その後 `solve!( problem )` を通じて解決（すなわち時間的に積分）することができます。

# 引数

  * `model   :: AbstractModel`、解かれる方程式の系。

例えば、`WaterWaves(param)` によって構築できます。

  * `initial :: InitialData`、初期データ。

例えば、`Init(η,v)` によって構築できます。ここで `η` は表面変形、`v` は表面での速度ポテンシャルのトレースの導関数です。

  * `times :: Times` は時間グリッドであり、`Times` 関数を使用して構築できます。

あるいは、単に `NamedTuple` を提供することもできます。 - `T` は積分の最終時間 - `dt` はタイムステップ - オプションで、`Ns` は計算されたデータの数、または `ns` は `ns` 計算ステップごとにデータを保存するためのもの（デフォルトでは、計算されたデータはすべて保存されます）。

## オプションのキーワード引数

  * `solver :: TimeSolver`、時間積分のためのソルバー（デフォルトは明示的ルンゲクッタ4次ソルバーです）。

例えば、`RK4(model)` または `RK4_naive()` によって構築できます。

  * `label   :: String` は将来の参照に使用されます（例：`plot_solution`）。
  * `verbose = false` の場合、情報は印刷されません（デフォルトは `true` です）。
