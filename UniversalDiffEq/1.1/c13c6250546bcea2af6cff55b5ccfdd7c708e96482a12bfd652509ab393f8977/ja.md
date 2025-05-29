```
CustomDerivatives(data::DataFrame,X::DataFrame,derivs!::Function,initial_parameters;kwargs ... )
```

データフレーム `X` が提供されると、モデルは共変量を使用して実行されます。引数 `X` には、時間 `t` に対応する列があり、残りの列には時間の値が含まれている必要があります。データフレームに含まれていない時間の値については、`X` の値が線形スプラインで補間されます。

`X` が提供される場合、derivs 関数は `derivs!(du,u,x,p,t)` の形式でなければなりません。ここで `x` は時間 `t` における共変量の値を持つベクトルです。

# kwargs

  * `time_column_name`: `data` と `X` における時間に対応する列の名前。デフォルトは `"time"` です。
  * `variable_column_name`: `X` における変数に対応する列の名前。デフォルトは `nothing` です。
  * `value_column_name`: `X` における共変量に対応する列の名前。デフォルトは `nothing` です。
  * `proc_weight`: プロセス誤差 $omega_{proc}$ の重み。デフォルトは `1.0` です。
  * `obs_weight`: 観測誤差 $omega_{obs}$ の重み。デフォルトは `1.0` です。
  * `reg_weight`: 正則化誤差 $omega_{reg}$ の重み。デフォルトは `10^-6` です。
  * `reg_type`: 正則化のタイプ、`"L1"` または `"L2"` 正則化のいずれか。デフォルトは `"L2"` です。
  * `l`: 予測のための外挿パラメータ。デフォルトは `0.25` です。
  * `extrap_rho`: 予測のための外挿パラメータ。デフォルトは `0.0` です。
  * `ode_solver`: 微分方程式の解を近似するためのメソッド。デフォルトは `Tsit5()` です。
  * `ad_method`: ODE ソルバーの導関数を評価するためのメソッド。デフォルトは `ForwardDiffSensitivity()` です。
