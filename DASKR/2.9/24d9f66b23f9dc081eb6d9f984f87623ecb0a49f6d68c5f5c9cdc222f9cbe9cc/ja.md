```julia
function daskr(;linear_solver=:Dense,
                  jac_upper=0,jac_lower=0,max_order = 5,
                  non_negativity_enforcement = 0,
                  non_negativity_enforcement_array = nothing,
                  max_krylov_iters = nothing,
                  num_krylov_vectors = nothing,
                  max_number_krylov_restarts = 5,
                  krylov_convergence_test_constant = 0.05,
                  exclude_algebraic_errors = false)
```

これは、よく知られたDASKRアルゴリズムのラッパーです。

DASKRは、微分代数方程式（DAE）の系のためのソルバーです。これは、各（暗黙的）時間ステップで発生する線形系の解法のための直接法と反復法（Krylov）の両方のオプションを含んでいます。DASKRは、DASPKパッケージのバリアントです[1]。DASPKのすべての機能に加えて、DASKRはDAEシステムを統合しながら、与えられた関数の根を見つける能力を含んでいます。

古いDASSLパッケージとは対照的に、DASKRは大規模な問題クラス（半明示的インデックス1システムを含む）のための一貫した初期条件を計算する手順を含んでいます[2]。この手順には、選択されたコンポーネントに対する不等式制約のオプションが含まれています。このパッケージには、局所誤差制御から代数コンポーネントを省略するオプションも含まれています。

### 線形ソルバーの選択

線形ソルバーの選択肢は次のとおりです：

  * `:Dense`
  * `:Banded`
  * `:SPIGMR`、Krylov法

### その他のキーワード引数

  * `jac_upper=0,jac_lower=0`：バンド付きヤコビアンの上部および下部バンドを設定するために使用されます。デフォルトは0です。線形ソルバーが`:Banded`でない限り無視されます。
  * `max_order = 5`：BDF法の最大次数。
  * `non_negativity_enforcement = 0`：解における非負性を強制するかどうか。デフォルトは`0`またはfalseで、`1`に設定することで有効にできます。
  * `non_negativity_enforcement_array = nothing`：状態のサブセットに対する非負性強制を指定するための0と1の配列。
  * `max_krylov_iters=nothing`：ステップを拒否する前のKrylov部分空間線形ソルバーの最大反復回数。デフォルトは`nothing`または自動検出です。
  * `num_krylov_vectors=nothing`：GMRESベクトル内の履歴状態の最大数。デフォルトは`nothing`または自動選択です。
  * `max_number_krylov_restarts=5`：これが何であるかを理解したら、問題を開くかPRを作成してください。
  * `krylov_convergence_test_constant = 0.05`：DASKRの収束テストにおけるいくつかの定数。
  * `exclude_algebraic_errors = false`：代数変数が適応的な時間ステッピング誤差チェックに含まれるかどうか。デフォルトはfalseです。
