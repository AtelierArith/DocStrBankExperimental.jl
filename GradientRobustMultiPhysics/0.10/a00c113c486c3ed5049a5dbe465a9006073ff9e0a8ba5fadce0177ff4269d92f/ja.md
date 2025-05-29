```
function TimeControlSolver(
    PDE::PDEDescription,                                        # PDEシステムの説明
    InitialValues::FEVector{T,Tv,Ti},                           # 初期値を含み、advance!メソッドの解を格納する
    TIR::Type{<:AbstractTimeIntegrationRule} = BackwardEuler;   # 時間積分ルール
    dt_operator = [],                                           # 各サブイテレーションに適用される時間微分の演算子（デフォルト：Identity）
    dt_action = [],                                             # 各サブイテレーションに適用される時間微分のアクション（デフォルト：NoAction）
    dt_is_nonlinear = [],                                          # 時間微分は非線形か？
    T_time = Float64,                                           # タイムステップと総時間の型
    kwargs...) where {T,Tv,Ti}                                  # 追加のソルバー引数
```

時間依存のソルバーを作成し、advance!で時間を進めることができます。FEVector Solutionは初期状態を格納しますが、現在の時間での解も格納します。引数TIRは使用する時間積分ルールを持ちます（例：BackwardEulerまたはCrankNicolson）。T_timeはタイムステップと総時間のNumberTypeを決定します。

キーワード引数：

  * subiterations: 各固定点イテレーションで一緒に解決されるべき方程式のサブセットの配列（各配列）。デフォルト: ''auto''
  * show*iteration*details: 各イテレーションの詳細（残差など）を表示します。デフォルト: true
  * timedependent_equations: 時間微分を取得すべき方程式の配列（TimeControlSolver専用）。デフォルト: Any[]
  * show_statistics: アセンブリ時間などの統計を表示します。デフォルト: false
  * skip*update: 行列の更新（j番目のサブイテレーション用）は、各skip*update[j]イテレーションごとに実行されます；-1は最初のイテレーションのみを意味します。デフォルト: [1]
  * linsolver: 線形ソルバーをエンコードする文字列、または自己定義ソルバーの型名（対応する例を参照）、またはExtendableSparse.AbstractFactorizationの型名。デフォルト: ''UMFPACK''
  * time: 時間依存データ関数が評価される時間、またはTimeControlSolverの初期時間。デフォルト: 0
  * parallel_storage: ループ内でストレージされた演算子を並列にアセンブルします。デフォルト: false
  * show*solver*config: 解決を開始する前に完全なソルバー構成を表示します。デフォルト: false
  * check*nonlinear*residual: 最後の非線形イテレーションで非線形残差をチェックします（非線形項の再アセンブルを1回引き起こします）。デフォルト: ''auto''
  * fixed_penalty: 固定自由度の値に使用されるペナルティ（例：Dirichlet境界データやグローバル制約による）。デフォルト: 1.0e60
  * target_residual: （非線形）残差がこの数より小さい場合、固定点イテレーションを停止します。デフォルト: 1.0e-10
  * maxiterations: 非線形イテレーションの最大数（TimeControlSolverは各タイムステップでそれだけ実行します）。デフォルト: ''auto''

TimeControlSolverのさらなる（非常に実験的な）オプション引数は次のとおりです：

  * dt_operator : 時間微分においてテスト関数に適用される演算子の（配列）(デフォルト: Identity)
  * dt_action : 時間微分においてアンズァツ関数に適用されるアクションの（配列）（パラメータなどを含む）
  * dt*is*nonlinear : 各タイムステップで再計算されるべき時間微分を決定するブール値の（配列）
