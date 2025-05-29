```
Options(;kws...) <: AbstractOptions
```

`equation_search`や他の関数のオプションを構築します。現在の引数は、https://github.com/MilesCranmer/PySR/discussions/115 からの中央値の値を使用して調整されています。

# 引数

  * `defaults`: `Options`に使用するデフォルトのセット。デフォルトは `nothing` で、現在のSymbolicRegressionのデフォルトオプションを単に取得します。ただし、`v"0.24.5"`のように、以前のバージョンのデフォルトを選択することもできます。
  * `binary_operators`: 使用する二項演算子（関数）のベクター。各演算子は2つの入力スカラーに対して定義され、1つの出力スカラーを持つ必要があります。すべての演算子は、無限大を除く実数全体で定義されている必要があり（無限大は入力される前に停止されます）、定義されていない場合は `NaN` を返す必要があります。速度のために、同じ型の2つの実数を入力として受け取り、同じ型を出力するように定義してください。SymbolicUtilsの簡略化バックエンドでは、任意の型を受け取るように演算子の一般的なメソッドを定義する必要があります。
  * `operator_enum_constructor`: 演算子列挙型を作成するために使用するコンストラクタ関数。デフォルトではOperatorEnumが使用されますが、GenericOperatorEnumのような別のコンストラクタを提供することもできます。コンストラクタは、キーワード引数 'binary*operators' と 'unary*operators' を受け入れる必要があります。
  * `unary_operators`: 同様ですが、単項演算子（1つの入力スカラー、出力スカラーを与える）用です。
  * `constraints`: 各演算子のサイズ制約を指定するペアの配列。二項演算子の制約は2タプル（例：`(-1, -1)`）であるべきで、単項演算子の制約は `Int` であるべきです。サイズ制約は、演算子の各引数のサブツリーのサイズの制限です。例：`[(^)=>(-1, 3)]` は、`^` 演算子が左引数で任意のサイズ（`-1`）を持つことができ、右引数で最大サイズ `3` を持つことを意味します。デフォルトは制約なしです。
  * `batching`: データ全体ではなく、小さなミニバッチのデータに基づいて進化するかどうか。
  * `batch_size`: バッチを使用する場合に使用するバッチサイズ。
  * `elementwise_loss`: 使用する要素ごとの損失関数。次の損失のいずれか、または `SupervisedLoss` 型の他の損失のいずれかであることができます。また、スカラーターゲット（左引数）とスカラー予測（右引数）を受け取り、スカラーを返す関数を渡すこともできます。これは予測データに対して平均化されます。重みが提供される場合、関数は重みスカラーのための3番目の引数を受け取る必要があります。含まれる損失:       回帰:           - `LPDistLoss{P}()`,           - `L1DistLoss()`,           - `L2DistLoss()`（平均二乗）,           - `LogitDistLoss()`,           - `HuberLoss(d)`,           - `L1EpsilonInsLoss(ϵ)`,           - `L2EpsilonInsLoss(ϵ)`,           - `PeriodicLoss(c)`,           - `QuantileLoss(τ)`,       分類:           - `ZeroOneLoss()`,           - `PerceptronLoss()`,           - `L1HingeLoss()`,           - `SmoothedL1HingeLoss(γ)`,           - `ModifiedHuberLoss()`,           - `L2MarginLoss()`,           - `ExpLoss()`,           - `SigmoidLoss()`,           - `DWDMarginLoss(q)`.
  * `loss_function`: あるいは、`tree::AbstractExpressionNode{T}`、`dataset::Dataset{T}`、および `options::AbstractOptions` の任意の関数として損失を再定義することができます。出力は非負のスカラー型 `T` である必要があります。これは、導関数やデータセット全体の相関を考慮に入れた損失を使用したい場合に便利です。特定の式のカスタム評価を使用することも意味します。`batching=true` を使用している場合、関数は4番目の引数 `idx` を受け入れる必要があります。これは `nothing`（フルデータセットを使用することを示す）か、バッチに使用するインデックスのベクターです。   例えば、

    ```
      function my_loss(tree, dataset::Dataset{T,L}, options)::L where {T,L}
          prediction, flag = eval_tree_array(tree, dataset.X, options)
          if !flag
              return L(Inf)
          end
          return sum((prediction .- dataset.y) .^ 2) / dataset.n
      end
    ```
  * `loss_function_expression`: `loss_function` に似ていますが、最初の引数として `AbstractExpression` を取ります。`TemplateExpressionSpec` に便利です。
  * `loss_scale`: スコアを計算する際に損失値がどのようにスケーリングされるかを決定します。オプションは次の通りです：

      * `:log`（デフォルト）：損失比の対数スケーリングを使用します。このモードは非負の損失値を必要とし、常に正の伝統的な損失関数に最適です。
      * `:linear`: 損失間の直接的な差を使用します。このモードは任意の損失値（負のものを含む）を処理し、特に尤度に基づくカスタム損失関数に便利です。
  * `expression_spec::AbstractExpressionSpec`: 検索に使用する式のタイプの仕様。例えば、`ExpressionSpec()`（デフォルト）。特定のケースには `TemplateExpressionSpec` や `ParametricExpressionSpec` を参照できます。
  * `populations`: 使用する方程式の集団の数。
  * `population_size`: 各集団の方程式の数。
  * `ncycles_per_iteration`: 各反復で考慮する世代の数。
  * `tournament_selection_n`: 各トーナメントで考慮される式の数。
  * `tournament_selection_p`: トーナメントで最も適応度の高い式が確率 `p` で選択され、次に適応度の高い式が確率 `p*(1-p)` で選択される、というように続きます。
  * `topn`: ホストプロセスに返す方程式の数、および名誉の殿堂に考慮する数。
  * `complexity_of_operators`: 各演算子に割り当てるべき複雑さ、定数または変数の出現。デフォルトでは、すべての演算子に対して1です。実数でも可能で、その場合、式の複雑さは最も近い整数に丸められます。例えば、[(^) => 3, sin => 2] の形式で入力します。
  * `complexity_of_constants`: 定数の使用に割り当てるべき複雑さ。デフォルトでは1です。
  * `complexity_of_variables`: 変数の使用に割り当てるべき複雑さ。これは異なる変数ごとの複雑さを示すベクターでも可能です。デフォルトでは1です。
  * `complexity_mapping`: あるいは、式を入力として受け取り、複雑さを返す関数を渡すことができます。これは `AbstractExpression` で動作し（`AbstractExpressionNode` に展開され）、整数を返す必要があります。
  * `alpha`: 正則進化中に方程式の突然変異を受け入れる確率は、exp(-delta_loss/(alpha * T)) で与えられ、Tは1から0に変化します。したがって、alpha=無限大はアニーリングなしと同じです。
  * `maxsize`: 検索中の方程式の最大サイズ。
  * `maxdepth`: 検索中の方程式の最大深さ。デフォルトでは、これがmaxsizeと等しく設定されています。
  * `parsimony`: 複雑さがどれだけ罰せられるかの乗数因子。
  * `dimensional_constraint_penalty`: 次元制約が違反された場合の加算因子。
  * `dimensionless_constants_only`: 次元のない定数のみを許可するかどうか。
  * `use_frequency`: 各複雑さでの方程式の相対的な割合に適応するパーシモニーを使用するかどうか。これにより、すべての複雑さに対して考慮される方程式の数がバランスされます。
  * `use_frequency_in_tournament`: 突然変異の受け入れ/拒否段階だけでなく、スコア内で上記の適応パーシモニーを使用するかどうか。
  * `adaptive_parsimony_scaling`: 損失内の適応パーシモニー項をどれだけスケーリングするか。検索が最も複雑な方程式の最適化に多くの時間を費やしている場合は、これを増やしてください。
  * `turbo`: 式を評価するために `LoopVectorization.@turbo` を使用するかどうか。これは大幅に高速化できますが、特定の演算子としか互換性がありません。*実験的！*
  * `bumper`: より高速な評価のためにBumper.jlを使用するかどうか。*実験的！*
  * `migration`: プロセス間で方程式を移行するかどうか。
  * `hof_migration`: 名誉の殿堂からプロセスに方程式を移行するかどうか。
  * `fraction_replaced`: 各サイクルの終わりに移行された方程式で置き換える各集団の割合。
  * `fraction_replaced_hof`: 各サイクルの終わりに名誉の殿堂の方程式で置き換える割合。
  * `should_simplify`: 方程式を簡略化するかどうか。カスタム目的を渡す場合、これは `false` に設定されます。
  * `should_optimize_constants`: 方程式内の定数を定期的に最適化するための最適化アルゴリズムを使用するかどうか。
  * `optimizer_algorithm`: 定数の最適化に使用するアルゴリズムを選択します。デフォルトは `Optim.BFGS(linesearch=LineSearches.BackTracking())` です。
  * `optimizer_nrestarts`: 定数の最適化のために考慮する異なるランダムな開始位置の数。
  * `optimizer_probability`: 特定の反復の終わりに定数の最適化を実行する確率。
  * `optimizer_iterations`: 実行する最適化反復の数。これは `Optim.Options` に `iterations` として渡されます。デフォルトは8です。
  * `optimizer_f_calls_limit`: 最適化中に許可される関数呼び出しの数。これは `Optim.Options` に `f_calls_limit` として渡されます。デフォルトは `10_000` です。
  * `optimizer_options`: 定数最適化の一般的なオプション。詳細については、`Optim.jl` パッケージの `Optim.Options` に関するドキュメントを参照してください。オプションは、`NamedTuple` としてここに提供できます（例：`(iterations=16,)`）、または `Dict` として（例：`Dict(:x_tol => 1.0e-32,)`）、または `Optim.Options` インスタンスとして提供できます。
  * `autodiff_backend`: 微分に使用するバックエンドで、`AbstractADType` のインスタンスである必要があります（`ADTypes.jl` を参照）。デフォルトは `nothing` で、これは `Optim.jl` が勾配を推定することを意味します（おそらく有限差分で）。また、Zygoteのための `:Zygote`、`:Enzyme` などのバックエンド型のシンボリックバージョンを渡すこともできます。ほとんどのバックエンドは機能せず、多くは互換性のために決して機能しませんが、一部のバックエンドのサポートは徐々に追加されています。
  * `perturbation_factor`: 定数を突然変異させるとき、(1+perturbation_factor)^(rand()+1) で乗算または除算します。
  * `probability_negate_constant`: 突然変異時に方程式内の定数を否定する確率。
  * `mutation_weights`: 突然変異の相対的な確率。構造体 `MutationWeights`（または任意の `AbstractMutationWeights`）をこれらのオプションに渡す必要があります。異なる重みについては、`MutationWeights` のドキュメントを参照してください。
  * `crossover_probability`: クロスオーバーを実行する確率。
  * `annealing`: シミュレーテッドアニーリングを使用するかどうか。
  * `warmup_maxsize_by`: 最大サイズを5から `maxsize` まで徐々に増加させるかどうか。非ゼロの場合、最大サイズに到達すべき検索の割合を指定します。
  * `verbosity`: デバッグステートメントを印刷するかどうか。
  * `print_precision`: 方程式を印刷する際に印刷する桁数。デフォルトは5です。
  * `output_directory`: 出力ファイルを保存するための基本ディレクトリ。ファイルは実行IDに応じたサブディレクトリに保存されます。デフォルトは `./outputs` です。
  * `save_to_file`: 検索中に方程式をファイルに保存するかどうか。
  * `bin_constraints`: `constraints` を参照してください。これは同じですが、二項演算子のみに指定されています（たとえば、二項演算子と単項演算子の両方である演算子がある場合）。
  * `una_constraints`: 同様に、単項演算子用です。
  * `seed`: 使用するランダムシード。`nothing` はシードを使用しません。
  * `progress`: 進行状況バー出力を使用するかどうか（`verbosity` は影響しません）。
  * `early_stop_condition`: Float - 平均損失がこの値を下回った場合に早期停止するかどうか。関数 - （損失、複雑さ）を引数として受け取り、真または偽を返す関数。
  * `timeout_in_seconds`: Float64 - 終了するまでの秒数（反復数の代わりに）。
  * `max_evals`: Int（またはNothing） - 実行する式の最大評価数。
  * `input_stream`: ユーザー入力を読み取るストリーム。デフォルトは `stdin` です。`stdin` からの読み取りに問題がある場合（ハングなど）、この引数に `devnull` を渡すことができます。
  * `skip_mutation_failures`: 失敗したり拒否されたりした突然変異を単にスキップするかどうか。突然変異した式を元の式で置き換えて通常通り進むのではなく。
  * `nested_constraints`: 演算子の組み合わせがネストできる回数を指定します。たとえば、`[sin => [cos => 0], cos => [cos => 2]]` は、`cos` が `sin` 内に現れることは決してないことを指定しますが、`sin` は無制限に自分自身とネストできます。2番目の項は、`cos` が `cos` 内で最大2回ネストできることを指定しているため、`cos(cos(cos(x)))` は許可されます（その中の `+` または `-` の任意の組み合わせも許可されます）が、`cos(cos(cos(cos(x))))` は許可されません。演算子が指定されていない場合、それは無制限にネストできると見なされます。これは、単項演算子と二項演算子の両方で使用される演算子がないことを要求します（例：`-` は引き算と否定の両方である可能性があります）。二項演算子の場合、両方の引数は同じ方法で扱われ、各引数の最大値が制約されます。
  * `deterministic`: `time()` への呼び出しではなく、出生時刻のためにグローバルカウンターを使用します。これにより、完全な解像度が得られ、したがって決定論的になります。ただし、スレッドセーフではなく、直列モードで使用する必要があります。
  * `define_helper_functions`: ツリーを構築および評価するためのヘルパー関数を定義するかどうか。
