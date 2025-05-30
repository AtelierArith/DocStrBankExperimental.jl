```
SolverConfig{T,TvG,TiG}(PDE::PDEDescription; kwargs...) where {T,TvG,TiG}
```

ソルバー構成を生成します（手動でアセンブリをトリガーするために使用できます）。

キーワード引数:

  * anderson_iterations: この数の以前の反復を使用してアンダーソン加速を行います（固定点反復の収束を加速/可能にすることを期待します）。デフォルト: 0
  * subiterations: 各固定点反復で一緒に解決されるべき方程式のサブセットの配列（各配列）。デフォルト: ''auto''
  * show*iteration*details: 各反復の詳細（残差など）を表示します。デフォルト: true
  * anderson_unknowns: アンダーソン加速に含めるべき未知数の配列。デフォルト: [1]
  * show_statistics: アセンブリ時間などの統計を表示します。デフォルト: false
  * anderson_metric: アンダーソン加速のための望ましい収束メトリックをエンコードする文字列（可能な値: ''l2'' または ''L2'' または ''H1''）。デフォルト: ''l2''
  * skip*update: 行列の更新（j 番目のサブ反復のため）は、各 skip*update[j] 反復ごとに実行されます; -1 は最初の反復のみを意味します。デフォルト: [1]
  * linsolver: 線形ソルバーをエンコードする文字列、または自己定義ソルバーの型名（対応する例を参照）、または ExtendableSparse.AbstractFactorization の型名。デフォルト: ''UMFPACK''
  * damping: 新しい反復を古い反復のこの部分で減衰させます（0 = 減衰なし）、また、インターフェースを持つ関数（old*iterate, new*iterate, fixed_dofs）が新しい減衰値を返すことも許可されます。デフォルト: 0
  * time: 時間依存データ関数が評価される時間、または TimeControlSolver の初期時間。デフォルト: 0
  * parallel_storage: ループのためにストレージされた演算子を並列にアセンブルします。デフォルト: false
  * show*solver*config: 解決を開始する前に完全なソルバー構成を表示します。デフォルト: false
  * anderson_damping: アンダーソン加速における減衰係数（1 = 減衰なし）。デフォルト: 1
  * check*nonlinear*residual: 最後の非線形反復における非線形残差をチェックします（非線形項の再アセンブリをもう一度引き起こします）。デフォルト: ''auto''
  * fixed_penalty: 固定自由度の値に使用されるペナルティ（例: ディリクレ境界データやグローバル制約による）。デフォルト: 1.0e60
  * target_residual: （非線形）残差がこの数より小さい場合、固定点反復を停止します。デフォルト: 1.0e-10
  * maxiterations: 非線形反復の最大数（TimeControlSolver は各タイムステップでその数を実行します）。デフォルト: ''auto''

```
