```
CustomModel(data::DataFrame,X::DataFrame, derivs!::Function, initial_parameters; kwargs ...)
```

DataFrame `data` から UDE モデルを構築し、共変量 `X` を持つ DataFrame、関数 `derivs`、およびパラメータ値 `initial_parameters` の初期推測を使用します。モデルの構造は、状態変数と観測値の関係、および損失関数を指定するためのキーワード引数によってさらに修正できます。これらの引数については、以下で個別に説明します。

# kwargs

link - 状態変数 `u` とパラメータ `p` の値を受け取り、観測値 `y` の推定値を返す関数 link*params - リンク関数のパラメータ。パラメータが使用されない場合は空の NamedTuple でも構いません observation*loss - 観測された状態と推定された状態の距離を説明する損失関数 observation*params - 観測損失関数のパラメータ - パラメータが必要ない場合は空の NamedTuple でも構いません process*loss - 観測された状態と予測された状態遷移の距離を説明する損失関数。 process*loss*params - プロセス損失のパラメータ。 state*variable*transform - 最適化に使用される変数から観測および予測関数で使用される状態変数へのマッピングを行う関数。 log*priors - モデルパラメータの事前確率 + ニューラルネットワークの正則化 time*column*name - データフレーム内の時間をインデックス付けする列 value*column*name - ロングフォーマットの共変量データセット内の変数を示す列 variable*column*name - ロングフォーマットの共変量データセット内の変数の値を示す列 reg*weight - ニューラルネットワークの正則化に与えられる重み reg_type - 正則化の関数形式 "L1" または "L2"
