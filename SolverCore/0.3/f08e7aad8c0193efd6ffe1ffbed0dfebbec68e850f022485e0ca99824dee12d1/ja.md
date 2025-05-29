```
GenericExecutionStats(nlp; ...)
GenericExecutionStats{T, S, V, Tsp}(;...)
```

`GenericExecutionStats`はソルバーの出力情報を格納するための構造体です。以下のフィールドを含みます：

  * `status`: ソルバーの出力を示します。完全なリストは`show_statuses()`を使用してください；
  * `solution`: ソルバーによって返される最終的な近似値（デフォルト：`nlp.meta.x0`のような初期化されていないベクトル）；
  * `objective`: `solution`における目的関数の値（デフォルト：`Inf`）；
  * `dual_feas`: `solution`における双対可行性ノルム（デフォルト：`Inf`）；
  * `primal_feas`: `solution`における一次可行性ノルム（デフォルト：制約がない場合は`0.0`、そうでない場合は`Inf`）；
  * `multipliers`: 制約に関するラグランジュ乗数（デフォルト：`nlp.meta.y0`のような初期化されていないベクトル）；
  * `multipliers_L`: 変数の下限に関するラグランジュ乗数（デフォルト：制約がある場合は`nlp.meta.x0`のような初期化されていないベクトル、ない場合はゼロ長のベクトル）；
  * `multipliers_U`: 変数の上限に関するラグランジュ乗数（デフォルト：制約がある場合は`nlp.meta.x0`のような初期化されていないベクトル、ない場合はゼロ長のベクトル）；
  * `iter`: ソルバーによって計算された反復回数（デフォルト：`-1`）；
  * `elapsed_time`: ソルバーによって計算された経過時間（デフォルト：`Inf`）；
  * `solver_specific::Dict{Symbol,Any}`: ソルバー固有の辞書。

コンストラクタは上記のフィールドのストレージを事前に確保します。`multipliers_L`および`multipliers_U`には、コンストラクタに渡すことで特別なストレージを使用できます。たとえば、問題に制約が少ない場合、これらの乗数はスパースベクトルに保持されることがあります。

以下のフィールドは、上記の情報が更新されており信頼できるかどうかを示します：

  * `solution_reliable`
  * `objective_reliable`
  * `residuals_reliable`（`dual_feas`および`primal_feas`用）
  * `multipliers_reliable`（`multipliers`用）
  * `bounds_multipliers_reliable`（`multipliers_L`および`multipliers_U`用）
  * `iter_reliable`
  * `time_reliable`
  * `solver_specific_reliable`。

`set_solution!()`、`set_objective!()`などのメソッドを使用してフィールドを設定すると、そのフィールドの値は信頼できるものとしてマークされます。

`reset!()`メソッドはすべてのフィールドを信頼できないものとしてマークします。

`nlp`はデフォルトのオプションフィールドを設定するために強く推奨されます。提供されない場合は、`solve!`の前に`reset!(stats, nlp)`を呼び出す必要があります。

他のすべての変数はキーワード引数として入力できます。

`GenericExecutionStats`は何も計算せず、単に格納するだけであることに注意してください。
