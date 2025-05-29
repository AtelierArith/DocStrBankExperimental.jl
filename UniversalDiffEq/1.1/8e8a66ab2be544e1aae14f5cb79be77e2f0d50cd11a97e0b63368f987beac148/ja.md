```
CustomDifference(data,step,initial_parameters;kwrags...)
```

ユーザー定義の差分方程式 `step` に基づいて、データセット `data` のための UDE モデルを構築します。モデルパラメータの初期推定値は、initial_parameters 引数で提供されます。 ...

# 引数

  * data: 観測の時間が `t` というラベルの列にあり、残りの列が各時間点での状態変数の値を持つ DataFrame オブジェクト。
  * step: `step(u,t,p)` の形の関数で、ここで `u` は状態変数の値、`p` はモデルパラメータです。
  * init_parameters: モデルパラメータを持つ `NamedTuple`。ニューラルネットワークのパラメータは `NN` というキーの下にリストされなければなりません。

# kwargs

  * `time_column_name`: `data` の中で時間に対応する列の名前。デフォルトは `"time"`。
  * `proc_weight`: プロセス誤差 $omega_{proc}$ の重み。デフォルトは `1.0`。
  * `obs_weight`: 観測誤差 $omega_{obs}$ の重み。デフォルトは `1.0`。
  * `reg_weight`: 正則化誤差 $omega_{reg}$ の重み。デフォルトは `10^-6`。
  * `reg_type`: 正則化のタイプ、`"L1"` または `"L2"` 正則化のいずれか。デフォルトは `"L2"`。
  * `l`: 予測のための外挿パラメータ。デフォルトは `0.25`。
  * `extrap_rho`: 予測のための外挿パラメータ。デフォルトは `0.0`。

...
