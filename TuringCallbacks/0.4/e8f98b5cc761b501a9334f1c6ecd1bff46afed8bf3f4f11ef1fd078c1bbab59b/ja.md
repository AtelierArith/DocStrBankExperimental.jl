```julia
struct TensorBoardCallback{L, F1, F2, F3}
```

`CoreLogging.AbstractLogger`をラップして、`AbstractMCMC.step`に渡すコールバックを構築します。

# 使用法

```
TensorBoardCallback(; kwargs...)
TensorBoardCallback(directory::string[, stats]; kwargs...)
TensorBoardCallback(lg::AbstractLogger[, stats]; kwargs...)
```

`TensorBoardCallback`のインスタンスを構築し、`lg`の代わりに`directory`が提供されている場合は`TBLogger`を作成します。

## 引数

  * `lg`: `TuringCallbacks.increment_step!`を実装する`AbstractLogger`のインスタンス。
  * `stats = nothing`: `OnlineStat`または変数名から統計推定器へのルックアップ。`stats isa OnlineStat`の場合、見えない変数名のために`stats`をコピーする`DefaultDict`を作成します。`isnothing`の場合、`Mean()`, `Variance()`, `KHist(num_bins)`を持つ`OnlineStats.Series`推定器を返すデフォルトコンストラクタを持つ`DefaultDict`が使用されます。

## キーワード引数

  * `num_bins::Int = 100`: ヒストグラムで使用するビンの数。
  * `filter = nothing`: 特定の変数と値のために統計をログするかどうかを決定するフィルター; 期待されるシグネチャは`filter(varname, value)`です。`isnothing`の場合、`exclude`と`include`から構築されたデフォルトフィルターが使用されます。
  * `exclude = String[]`: 空でない場合、これらの変数はログされません。
  * `include = String[]`: 空でない場合、これらの変数のみがログされます。
  * `include_extras::Bool = true`: 遷移からの追加統計を含める。
  * `extras_include = String[]`: 空でない場合、これらの追加統計のみがログされます。
  * `extras_exclude = String[]`: 空でない場合、これらの追加統計はログされません。
  * `extras_filter = nothing`: 追加統計をログするかどうかを決定するフィルター; 期待されるシグネチャは`filter(extra, value)`です。`isnothing`の場合、`extras_exclude`と`extras_include`から構築されたデフォルトフィルターが使用されます。
  * `include_hyperparams::Bool = true`: ハイパーパラメータを含める。
  * `hyperparam_include = String[]`: 空でない場合、これらのハイパーパラメータのみがログされます。
  * `hyperparam_exclude = String[]`: 空でない場合、これらのハイパーパラメータはログされません。
  * `hyperparam_filter = nothing`: ハイパーパラメータをログするかどうかを決定するフィルター; 期待されるシグネチャは`filter(hyperparam, value)`です。`isnothing`の場合、`hyperparam_exclude`と`hyperparam_include`から構築されたデフォルトフィルターが使用されます。
  * `directory::String = nothing`: 指定された場合、`comment`と共にログディレクトリを定義するために使用されます。
  * `comment::String = nothing`: 指定された場合、`directory`と共にログディレクトリを定義するために使用されます。

# フィールド

  * `logger::Base.CoreLogging.AbstractLogger`: 基本のロガー。
  * `stats::Any`: 変数名から統計推定へのルックアップ。
  * `variable_filter::Any`: 特定の変数の統計を含めるかどうかを決定するフィルター。
  * `include_extras::Bool`: 遷移からの追加統計を含める。
  * `extras_filter::Any`: 特定の追加統計を含めるかどうかを決定するフィルター。
  * `include_hyperparams::Bool`: ハイパーパラメータを含める。
  * `hyperparam_filter::Any`: 特定のハイパーパラメータを含めるかどうかを決定するフィルター。
  * `param_prefix::String`: 実現/パラメータのログに使用されるプレフィックス
  * `extras_prefix::String`: 追加統計のログに使用されるプレフィックス
