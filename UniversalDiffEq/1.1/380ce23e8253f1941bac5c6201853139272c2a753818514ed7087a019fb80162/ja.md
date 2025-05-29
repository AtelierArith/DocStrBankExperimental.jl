```
MultiCustomDerivatives(data,derivs!,initial_parameters;kwargs...)
```

複数の時系列を同時にトレーニングできるUDEモデルを構築します。ユーザー定義の導関数関数は、データセット内の時系列をインデックスする追加の引数 `i` を許可する必要があります（例：`derivs!(du,u,i,)`）。`data` は、時間引数が `t` というラベルの列に配置され、各時系列のユニークなインデックスを持つ2番目の列を持つDataFrameオブジェクトです。残りの列には、各時点および各時系列の状態変数の観測値が含まれています。

# kwargs

  * `time_column_name`: `data` 内の時間に対応する列の名前。デフォルトは `"time"`。
  * `series_column_name`: `data` 内の系列に対応する列の名前。デフォルトは `"series"`。
  * `variable_column_name`: `data` 内の変数に対応する列の名前。デフォルトは `"variable"`。
  * `value_column_name`: `data` 内の共変量に対応する列の名前。デフォルトは `"value"`。
  * `proc_weight`: プロセス誤差 `omega_{proc}` の重み。デフォルトは `1.0`。
  * `obs_weight`: 観測誤差 `omega_{obs}` の重み。デフォルトは `1.0`。
  * `reg_weight`: 正則化誤差 `omega_{reg}` の重み。デフォルトは `10^-6`。
  * `reg_type`: 正則化のタイプ、`"L1"` または `"L2"` 正則化のいずれか。デフォルトは `"L2"`。
  * `l`: 予測のための外挿パラメータ。デフォルトは `0.25`。
  * `extrap_rho`: 予測のための外挿パラメータ。デフォルトは `0.0`。
  * `ode_solver`: 微分方程式の解を近似するためのメソッド。デフォルトは `Tsit5()`。
  * `ad_method`: ODEソルバーの導関数を評価するためのメソッド。デフォルトは `ForwardDiffSensitivity()`。
