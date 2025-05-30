```julia
ItemIntegrator(
    operators;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, Float64, ON_CELLS, Float64, Int32, GradientRobustMultiPhysics.NoAction}
ItemIntegrator(
    operators,
    action;
    T,
    AT,
    regions,
    name
) -> GradientRobustMultiPhysics.AssemblyPattern{ItemIntegrator, Float64, ON_CELLS, Float64, Int32}

```

ItemIntegratorアセンブリパターンを作成します:

  * operators : 対応するFESpaceに対して評価されるべきオペレーター（最後のものはテスト関数を指します）
  * action    : 入力（最後のオペレーター評価を除く）を受け取り、結果を計算するインターフェースのカーネルを持つアクション（result, input, kwargs）で、結果はテスト関数評価とドット積されます（アクションが指定されていない場合、全入力ベクトルがテスト関数オペレーター評価とドット積されます）

オプション引数:

  * T         : 評価出力の期待されるNumberType
  * AT        : ItemIntegratorが評価されるグリッドのエンティティを指定します
  * regions   : オペレーターがアセンブルされるべき領域を指定します。デフォルトの[0]はすべての領域を意味します
  * name      : 印刷メッセージで使用されるこのLinearFormの名前
