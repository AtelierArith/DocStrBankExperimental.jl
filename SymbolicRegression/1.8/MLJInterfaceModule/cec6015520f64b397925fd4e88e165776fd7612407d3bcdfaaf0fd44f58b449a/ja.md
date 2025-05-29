```
SRRegressor
```

進化的探索を通じて記号回帰を構築するためのモデルタイプで、[SymbolicRegression.jl](https://github.com/MilesCranmer/SymbolicRegression.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
SRRegressor = @load SRRegressor pkg=SymbolicRegression
```

`model = SRRegressor()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトをオーバーライドするには、`SRRegressor(defaults=...)`のようにキーワード引数を提供します。

単一ターゲットの記号回帰回帰器（`SRRegressor`）は、入力変数のセットから単一のターゲット変数を予測する記号表現を検索します。すべてのデータは`Continuous`であると仮定されます。探索は進化的アルゴリズムを使用して行われます。このアルゴリズムは、https://arxiv.org/abs/2305.01582の論文で説明されています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X, y)
```

または

```
mach = machine(model, X, y, w)
```

ここで：

  * `X`は、列が`Continuous`のscitypeを持つ任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。発見された表現の変数名は、利用可能な場合、`X`の列名から取られます。`X`の列の単位（単位には`DynamicQuantities`を使用）により、次元分析が使用されます。
  * `y`はターゲットで、要素のscitypeが`Continuous`の任意の`AbstractVector`です。scitypeは`scitype(y)`で確認できます。`y`の単位（単位には`DynamicQuantities`を使用）により、次元分析が使用されます。
  * `w`は観測重みで、`nothing`（デフォルト）または要素のscitypeが`Count`または`Continuous`の`AbstractVector`のいずれかです。

`fit!(mach)`を使用してマシンをトレーニングし、`report(mach)`で発見された表現を検査し、`predict(mach, Xnew)`で新しいデータに対して予測します。他の回帰器とは異なり、記号回帰はトレーニングされたモデルのリストを保存します。このリストから選択されるモデルは、デフォルトで精度と複雑さのバランスを取る`selection_method`キーワード引数によって定義されます。予測時に、`data`と`idx`というキーを持つ名前付きタプルを渡すことでこれをオーバーライドできます。

# ハイパーパラメータ

  * `defaults`: `Options`に使用するデフォルトのセット。デフォルトの`nothing`は、SymbolicRegressionの現在のバージョンからデフォルトオプションを単に取得します。ただし、`v"0.24.5"`のように、以前のバージョンからデフォルトを選択することもできます。
  * `binary_operators`: 使用する二項演算子（関数）のベクトル。各演算子は2つの入力スカラーに対して定義され、1つの出力スカラーを返す必要があります。すべての演算子は、無限大を除く実数全体で定義されている必要があります（これらは入力される前に停止されます）、または定義されていない場合は`NaN`を返す必要があります。速度のために、同じ型の2つの実数を入力として受け取り、同じ型を出力するように定義してください。SymbolicUtilsの簡略化バックエンドでは、任意の型を受け取るように演算子の一般的なメソッドを定義する必要があります。
  * `unary_operators`: 同様ですが、単項演算子（1つの入力スカラー、出力スカラーを返す）用です。
  * `constraints`: 各演算子のサイズ制約を指定するペアの配列。二項演算子の制約は2タプル（例：`(-1, -1)`）で、単項演算子の制約は`Int`である必要があります。サイズ制約は、演算子の各引数のサブツリーのサイズの制限です。例：`[(^)=>(-1, 3)]`は、`^`演算子が左引数で任意のサイズ（`-1`）を持つことができるが、右引数で最大サイズ`3`を持つことを意味します。デフォルトは制約なしです。
  * `batching`: データの小さなミニバッチに基づいて進化するか、全体のデータセットに基づいて進化するか。
  * `batch_size`: バッチ処理を使用する場合に使用するバッチサイズ。
  * `elementwise_loss`: 使用する要素ごとの損失関数。次の損失のいずれか、または`SupervisedLoss`型の他の損失のいずれかである可能性があります。また、スカラーターゲット（左引数）とスカラー予測（右引数）を受け取り、スカラーを返す関数を渡すこともできます。これは予測データに対して平均化されます。重みが提供される場合、関数は重みスカラーのための3番目の引数を受け取る必要があります。含まれる損失：       回帰:           - `LPDistLoss{P}()`,           - `L1DistLoss()`,           - `L2DistLoss()`（平均二乗）、           - `LogitDistLoss()`,           - `HuberLoss(d)`,           - `L1EpsilonInsLoss(ϵ)`,           - `L2EpsilonInsLoss(ϵ)`,           - `PeriodicLoss(c)`,           - `QuantileLoss(τ)`,       分類:           - `ZeroOneLoss()`,           - `PerceptronLoss()`,           - `L1HingeLoss()`,           - `SmoothedL1HingeLoss(γ)`,           - `ModifiedHuberLoss()`,           - `L2MarginLoss()`,           - `ExpLoss()`,           - `SigmoidLoss()`,           - `DWDMarginLoss(q)`.
  * `loss_function`: あるいは、`tree::AbstractExpressionNode{T}`、`dataset::Dataset{T}`、および`options::AbstractOptions`の任意の関数として使用される損失を再定義できます。出力が非負のスカラー`T`である限り、これは有用です。これは、導関数やデータセット全体の相関を考慮に入れた損失を使用したい場合に便利です。特定の表現のためにカスタム評価を使用することもできます。`batching=true`を使用している場合、関数は4番目の引数`idx`を受け入れる必要があります。これは`nothing`（フルデータセットを使用することを示す）またはバッチに使用するインデックスのベクトルです。   例えば、

    ```
      function my_loss(tree, dataset::Dataset{T,L}, options)::L where {T,L}
          prediction, flag = eval_tree_array(tree, dataset.X, options)
          if !flag
              return L(Inf)
          end
          return sum((prediction .- dataset.y) .^ 2) / dataset.n
      end
    ```
  * `loss_function_expression`: `loss_function`に似ていますが、最初の引数として`AbstractExpression`を受け取ります。`TemplateExpressionSpec`に便利です。
  * `expression_spec::AbstractExpressionSpec`: 探索に使用する表現のタイプの仕様。例えば、`ExpressionSpec()`（デフォルト）。特定のケースについては、`TemplateExpressionSpec`や`ParametricExpressionSpec`も参照できます。
  * `populations`: 使用する方程式の集団の数。
  * `population_size`: 各集団の方程式の数。
  * `ncycles_per_iteration`: 各反復で考慮する世代の数。
  * `tournament_selection_n`: 各トーナメントで考慮される表現の数。
  * `tournament_selection_p`: トーナメントで最も適応度の高い表現が確率`p`で選択され、次に適応度の高いものが確率`p*(1-p)`で選択される、というように続きます。
  * `topn`: ホストプロセスに返す方程式の数、および名誉の殿堂に考慮される方程式の数。
  * `complexity_of_operators`: 各演算子および定数または変数の出現に割り当てるべき複雑さ。デフォルトでは、すべての演算子に対して1です。実数でも可能で、その場合、表現の複雑さは最も近い整数に丸められます。例えば、[(^) => 3, sin => 2]の形式で入力します。
  * `complexity_of_constants`: 定数の使用に割り当てるべき複雑さ。デフォルトでは、これは1です。
  * `complexity_of_variables`: 変数の使用に割り当てるべき複雑さで、異なる変数ごとの複雑さを示すベクトルでもかまいません。デフォルトでは、これは1です。
  * `complexity_mapping`: あるいは、表現を入力として受け取り、複雑さを返す関数を渡すことができます。これは`AbstractExpression`（および`AbstractExpressionNode`に展開される）で動作し、整数を返す必要があります。
  * `alpha`: 正則進化中に方程式の突然変異を受け入れる確率は、exp(-delta_loss/(alpha * T))で与えられ、Tは1から0に変化します。したがって、alpha=infiniteはアニーリングなしと同じです。
  * `maxsize`: 探索中の方程式の最大サイズ。
  * `maxdepth`: 探索中の方程式の最大深さ。デフォルトでは、これはmaxsizeと等しく設定されています。
  * `parsimony`: 複雑さがどれだけ罰せられるかの乗数係数。
  * `dimensional_constraint_penalty`: 次元制約が違反された場合の加算係数。
  * `dimensionless_constants_only`: 次元のない定数のみを許可するかどうか。
  * `use_frequency`: 各複雑さで考慮される方程式の相対的な割合に適応するパーシモニーを使用するかどうか。これにより、すべての複雑さに対してバランスの取れた数の方程式が考慮されることが保証されます。
  * `use_frequency_in_tournament`: 突然変異の受け入れ/拒否段階だけでなく、スコア内で上記の適応パーシモニーを使用するかどうか。
  * `adaptive_parsimony_scaling`: 損失内の適応パーシモニー項をどれだけスケーリングするか。探索が最も複雑な方程式の最適化に多くの時間を費やしている場合は、これを増やしてください。
  * `turbo`: 表現を評価するために`LoopVectorization.@turbo`を使用するかどうか。これは大幅に高速化できますが、特定の演算子としか互換性がありません。*実験的！*
  * `bumper`: より高速な評価のためにBumper.jlを使用するかどうか。*実験的！*
  * `migration`: プロセス間で方程式を移行するかどうか。
  * `hof_migration`: 名誉の殿堂からプロセスに方程式を移行するかどうか。
  * `fraction_replaced`: 各サイクルの終わりに移行された方程式で置き換える各集団の割合。
  * `fraction_replaced_hof`: 各サイクルの終わりに名誉の殿堂の方程式で置き換える割合。
  * `should_simplify`: 方程式を簡略化するかどうか。カスタム目的を渡す場合、これは`false`に設定されます。
  * `should_optimize_constants`: 方程式内の定数を定期的に最適化するための最適化アルゴリズムを使用するかどうか。
  * `optimizer_algorithm`: 定数の最適化に使用するアルゴリズムを選択します。デフォルトは`Optim.BFGS(linesearch=LineSearches.BackTracking())`です。
  * `optimizer_nrestarts`: 定数の最適化のために考慮する異なるランダムな開始位置の数。
  * `optimizer_probability`: 特定の反復の終わりに定数の最適化を実行する確率。
  * `optimizer_iterations`: 実行する最適化反復の数。これは`Optim.Options`に`iterations`として渡されます。デフォルトは8です。
  * `optimizer_f_calls_limit`: 最適化中に許可される関数呼び出しの数。これは`Optim.Options`に`f_calls_limit`として渡されます。デフォルトは`10_000`です。
  * `optimizer_options`: 定数最適化の一般的なオプション。詳細については、`Optim.jl`パッケージの`Optim.Options`に関するドキュメントを参照してください。オプションは、`NamedTuple`としてここに提供できます（例：`(iterations=16,)`）、または`Dict`として（例：`Dict(:x_tol => 1.0e-32,)`）、または`Optim.Options`インスタンスとして提供できます。
  * `autodiff_backend`: 微分に使用するバックエンドで、`AbstractADType`のインスタンスである必要があります（`ADTypes.jl`を参照）。デフォルトは`nothing`で、これは`Optim.jl`が勾配を推定することを意味します（おそらく有限差分で）。バックエンドタイプの記号バージョン（例：Zygoteの場合は`:Zygote`、`Enzyme`など）を渡すこともできます。ほとんどのバックエンドは機能しないか、互換性のために機能しないことが多いですが、一部のバックエンドのサポートは徐々に追加されています。
  * `perturbation_factor`: 定数を突然変異させるとき、(1+perturbation_factor)^(rand()+1)で乗算または除算します。
  * `probability_negate_constant`: 突然変異時に方程式内の定数を否定する確率。
  * `mutation_weights`: 突然変異の相対的な確率。構造体`MutationWeights`（または任意の`AbstractMutationWeights`）をこれらのオプションに渡す必要があります。異なる重みについては、`MutationWeights`のドキュメントを参照してください。
  * `crossover_probability`: 交差を実行する確率。
  * `annealing`: シミュレーテッドアニーリングを使用するかどうか。
  * `warmup_maxsize_by`: `maxsize`まで最大サイズを徐々に増加させるかどうか。非ゼロの場合、最大サイズに達するまでの探索の割合を指定します。
  * `verbosity`: デバッグステートメントを印刷するかどうか。
  * `print_precision`: 方程式を印刷する際に印刷する桁数。デフォルトは5です。
  * `output_directory`: 出力ファイルを保存するための基本ディレクトリ。ファイルは実行IDに応じたサブディレクトリに保存されます。デフォルトは`./outputs`です。
  * `save_to_file`: 探索中に方程式をファイルに保存するかどうか。
  * `bin_constraints`: `constraints`を参照してください。これは同じですが、二項演算子のみに指定されています（たとえば、二項演算子と単項演算子の両方である演算子がある場合）。
  * `una_constraints`: 同様に、単項演算子用です。
  * `seed`: 使用するランダムシード。`nothing`はシードを使用しません。
  * `progress`: 進捗バー出力を使用するかどうか（`verbosity`は影響しません）。
  * `early_stop_condition`: 浮動小数点 - 平均損失がこの値を下回った場合に早期に停止するかどうか。関数 - （損失、複雑さ）を引数として受け取り、真または偽を返す関数。
  * `timeout_in_seconds`: Float64 - 終了するまでの時間（反復数の代わりに）。
  * `max_evals`: Int（またはNothing） - 実行する表現の最大評価数。
  * `input_stream`: ユーザー入力を読み取るストリーム。デフォルトは`stdin`です。`stdin`からの読み取りに問題がある場合（ハングなど）、この引数に`devnull`を渡すことができます。
  * `skip_mutation_failures`: 失敗したり拒否されたりした突然変異を単にスキップするか、突然変異した表現を元の表現で置き換えて通常通り進むかどうか。
  * `nested_constraints`: 演算子の組み合わせをネストできる回数を指定します。たとえば、`[sin => [cos => 0], cos => [cos => 2]]`は、`cos`が`sin`内に現れることは決してないことを指定しますが、`sin`は無制限に自分自身とネストできます。2番目の項は、`cos`が`cos`内で最大2回ネストできることを指定します。したがって、`cos(cos(cos(x)))`は許可されます（その中の`+`または`-`の任意の組み合わせも許可されます）が、`cos(cos(cos(cos(x))))`は許可されません。演算子が指定されていない場合、それは無制限にネストできると見なされます。これは、単項演算子と二項演算子の両方で使用される演算子がないことを要求します（例：`-`は引き算と否定の両方である可能性があります）。二項演算子の場合、両方の引数は同じ方法で扱われ、各引数の最大値が制約されます。
  * `deterministic`: `time()`への呼び出しではなく、出生時刻のためにグローバルカウンタを使用します。これにより、完全な解像度が得られ、したがって決定論的になります。ただし、スレッドセーフではなく、直列モードで使用する必要があります。
  * `define_helper_functions`: ツリーを構築および評価するためのヘルパー関数を定義するかどうか。
  * `niterations::Int=10`: 探索を実行する反復の数。反復が多いほど、結果が改善されます。
  * `parallelism=:multithreading`: 使用する並列モード。オプションは`:multithreading`、`:multiprocessing`、および`:serial`です。デフォルトでは、マルチスレッドが使用されます。マルチスレッドはメモリを少なく使用しますが、マルチプロセッシングはマルチノード計算を処理できます。`:multithreading`モードを使用している場合、利用可能なスレッド数がjuliaに使用されます。`:multiprocessing`を使用している場合、`procs`が未設定の場合、`numprocs`プロセスが動的に作成されます。すでにプロセスを割り当てている場合は、それらを`procs`引数に渡すと使用されます。文字列をシンボルの代わりに渡すこともできます（例：`"multithreading"`）。
  * `numprocs::Union{Int, Nothing}=nothing`: `equation_search`が自動的にこれを設定する場合に使用するプロセスの数。デフォルトでは`4`ですが、任意の数（利用可能なコアの数以下）を選択できます。
  * `procs::Union{Vector{Int}, Nothing}=nothing`: `procs = addprocs()`および`@everywhere`で手動で分散実行を設定した場合、`procs`をこのキーワード引数に渡します。
  * `addprocs_function::Union{Function, Nothing}=nothing`: マルチプロセッシングを使用している場合（`parallelism=:multithreading`）、手動で`procs`を渡さない場合、`addprocs`を使用して動的に割り当てられます。ただし、`addprocs`の代わりに使用するカスタム関数を渡すこともできます。この関数は、使用するプロセスの数と`lazy`キーワード引数を受け取る単一の位置引数を取る必要があります。たとえば、slurmクラスターで設定されている場合、`addprocs_function = addprocs_slurm`を渡すことができます。
  * `heap_size_hint_in_bytes::Union{Int,Nothing}=nothing`: Julia 1.9+では、Juliaプロセスで`--heap-size-hint`フラグを設定し、プロセスが推奨サイズに近づいたときにガーベジコレクションを推奨します。これは、各プロセスが独立したメモリを持つ長時間実行される分散ジョブにとって重要で、メモリ不足エラーを回避するのに役立ちます。デフォルトでは、これは`Sys.free_memory() / numprocs`に設定されています。
  * `worker_imports::Union{Vector{Symbol},Nothing}=nothing`: 各ワーカーで追加のモジュールをインポートしたい場合、ここにシンボルのベクトルとして渡します。デフォルトでは、必要に応じて自動的にいくつかの拡張がロードされます。
  * `runtests::Bool=true`: 探索を開始する前に（迅速な）テストを実行して、ホスト環境に関連する方程式探索中に問題が発生するかどうかを確認するかどうか。
  * `run_id::Union{String,Nothing}=nothing`: 実行の一意の識別子。これは、実行からの出力を`outputs`ディレクトリに保存するために使用されます。指定されていない場合、一意のIDが生成されます。
  * `loss_type::Type=Nothing`: 渡したデータとは異なる損失の型を使用したい場合は、ここに型を指定します。複素データ`::Complex{L}`を渡すと、損失型は自動的に`L`に設定されます。
  * `selection_method::Function`: `predict`で使用するためにパレートフロンティアから表現を選択する関数。例については`SymbolicRegression.MLJInterfaceModule.choose_best`を参照してください。この関数は、使用する表現のインデックスを指定する単一の整数を返す必要があります。デフォルトでは、1.5倍の最小損失の閾値に達する表現のスコア（ポンドごとの評価）を最大化します。予測時にこれをオーバーライドするには、`data`と`idx`というキーを持つ名前付きタプルを`predict`に渡すことができます。詳細については操作セクションを参照してください。
  * `dimensions_type::AbstractDimensions`: データの単位を保存する際に使用する次元の型。デフォルトでは、これは`DynamicQuantities.SymbolicDimensions`です。

# 操作

  * `predict(mach, Xnew)`: 特徴`Xnew`を考慮してターゲットの予測を返します。`X`と同じscitypeを持つ必要があります。予測に使用される表現は、`selection_method`関数によって定義され、`report(mach).best_idx`を表示することで確認できます。
  * `predict(mach, (data=Xnew, idx=i))`: 特徴`Xnew`を考慮してターゲットの予測を返します。`data`と`idx`というキーを持つ名前付きタプルを渡すことで、`idx`で評価したい方程式を指定できます。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `best_idx::Int`: `selection_method`関数によって決定されたパレートフロンティア内の最良の表現のインデックス。`predict`で`data`と`idx`というキーを持つ名前付きタプルを渡すことでオーバーライドできます。
  * `equations::Vector{Node{T}}`: 探索によって発見された表現で、支配的なパレートフロンティア（すなわち、各複雑さに対して見つかった最良の表現）で表現されます。`T`は渡されたデータの要素型に等しいです。
  * `equation_strings::Vector{String}`: 探索によって発見された表現で、簡単に検査できるように文字列として表現されます。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `best_idx::Int`: `selection_method`関数によって決定されたパレートフロンティア内の最良の表現のインデックス。`predict`で`data`と`idx`というキーを持つ名前付きタプルを渡すことでオーバーライドできます。
  * `equations::Vector{Node{T}}`: 探索によって発見された表現で、支配的なパレートフロンティア（すなわち、各複雑さに対して見つかった最良の表現）で表現されます。
  * `equation_strings::Vector{String}`: 探索によって発見された表現で、簡単に検査できるように文字列として表現されます。
  * `complexities::Vector{Int}`: パレートフロンティア内の各表現の複雑さ。
  * `losses::Vector{L}`: モデルで指定された損失関数に従ったパレートフロンティア内の各表現の損失。型`L`は損失型で、通常は渡されたデータの要素型（すなわち`T`）と同じですが、複素データ型が渡された場合は異なることがあります。
  * `scores::Vector{L}`: 複雑さと損失の両方を考慮したメトリックで、パレートフロンティアに沿った前の表現に対する複雑さの変化に対する損失の対数の変化に等しいです。大きなスコアは、表現がデータを生成する真の表現である可能性が高いことを示すことを目指しますが、これは非常に問題依存的であり、一般的に他のいくつかの要因も考慮する必要があります。

# 例

```julia
using MLJ
SRRegressor = @load SRRegressor pkg=SymbolicRegression
X, y = @load_boston
model = SRRegressor(binary_operators=[+, -, *], unary_operators=[exp], niterations=100)
mach = machine(model, X, y)
fit!(mach)
y_hat = predict(mach, X)
# 使用された方程式を表示：
r = report(mach)
println("使用された方程式:", r.equation_strings[r.best_idx])
```

単位と変数名を使用した例：

```julia
using MLJ
using DynamicQuantities
SRegressor = @load SRRegressor pkg=SymbolicRegression

X = (; x1=rand(32) .* us"km/h", x2=rand(32) .* us"km")
y = @. X.x2 / X.x1 + 0.5us"h"
model = SRRegressor(binary_operators=[+, -, *, /])
mach = machine(model, X, y)
fit!(mach)
y_hat = predict(mach, X)
# 使用された方程式を表示：
r = report(mach)
println("使用された方程式:", r.equation_strings[r.best_idx])
```

[`MultitargetSRRegressor`](@ref)も参照してください。
