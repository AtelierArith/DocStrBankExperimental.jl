```
function solve(
    PDE::PDEDescription,
    FES;
    kwargs...)
```

与えられた FESpace(s) FES に対して PDE の解を FEVector として返します（PDE の未知数を離散化するために使用されます）。非線形問題のために非ゼロの初期値を提供するには、solve! 関数を使用する必要があります。

この関数は CommonSolve.solve インターフェースを拡張し、PDEDescription は ProblemType の役割を果たし、FES は SolverType の役割を果たします。

キーワード引数:

  * anderson_iterations: この数の以前の反復を使用してアンダーソン加速を行います（固定点反復の収束を加速/可能にすることを期待します）。デフォルト: 0
  * subiterations: 各固定点反復で一緒に解決されるべき方程式のサブセットの配列（各配列）。デフォルト: ''auto''
  * show*iteration*details: 各反復の詳細（残差など）を表示します。デフォルト: true
  * anderson_unknowns: アンダーソン加速に含めるべき未知数の配列。デフォルト: [1]
  * reltol: 線形ソルバーの相対許容誤差（反復的な場合）。デフォルト: 1.0e-12
  * show_statistics: アセンブリ時間などの統計を表示します。デフォルト: false
  * anderson_metric: アンダーソン加速のための望ましい収束メトリックをエンコードする文字列（可能な値: ''l2'' または ''L2'' または ''H1''）。デフォルト: ''l2''
  * skip*update: 行列の更新（j 番目のサブ反復のため）は、各 skip*update[j] 反復で実行されます; -1 は最初の反復のみを意味します。デフォルト: [1]
  * linsolver: LinearSolve.jl からの任意の AbstractFactorization（デフォルト = UMFPACKFactorization）。デフォルト: LinearSolve.UMFPACKFactorization(true, true)
  * damping: 新しい反復を古い反復のこの部分で減衰させます（0 = 減衰なし）、また、インターフェースを持つ関数も許可されます（old*iterate, new*iterate, fixed_dofs）で新しい減衰値を返します。デフォルト: 0
  * time: 時間依存データ関数が評価される時間または TimeControlSolver の初期時間。デフォルト: 0
  * parallel_storage: ループのためにストレージされた演算子を並列にアセンブルします。デフォルト: false
  * show*solver*config: 解決を開始する前に完全なソルバー構成を表示します。デフォルト: false
  * anderson_damping: アンダーソン加速における減衰係数（1 = 減衰なし）。デフォルト: 1
  * abstol: 線形ソルバーの絶対許容誤差（反復的な場合）。デフォルト: 1.0e-12
  * check*nonlinear*residual: 最後の非線形反復で非線形残差をチェックします（非線形項の再アセンブルをもう一度引き起こします）。デフォルト: ''auto''
  * fixed_penalty: 固定自由度の値に使用されるペナルティ（例: ディリクレ境界データやグローバル制約による）。デフォルト: 1.0e60
  * target_residual: 絶対（非線形）残差がこの数より小さい場合、固定点反復を停止します。デフォルト: 1.0e-12
  * maxiterations: 非線形反復の最大数（TimeControlSolver は各タイムステップでその数を実行します）。デフォルト: ''auto''

サブ反復と検出された/構成された非線形性に応じて、全システムは直接1ステップで解決されるか、固定点反復を介して解決されます。
