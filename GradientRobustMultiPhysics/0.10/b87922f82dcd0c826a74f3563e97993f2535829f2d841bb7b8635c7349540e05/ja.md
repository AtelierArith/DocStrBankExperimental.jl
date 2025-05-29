```julia
DiscreteLinearForm(
    operators,
    FES::Array{<:GradientRobustMultiPhysics.FESpace{Tv, Ti}, 1};
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{LinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteLinearForm(
    operators,
    FES::Array{<:GradientRobustMultiPhysics.FESpace{Tv, Ti}, 1},
    action;
    T,
    AT,
    regions,
    name
) -> GradientRobustMultiPhysics.AssemblyPattern{LinearForm, Float64, ON_CELLS}

```

次の内容に基づいて（離散）LinearForm アセンブリパターンを作成します：

  * operators : 対応する FESpace に対して評価されるべき演算子（最後のものはテスト関数を指します）
  * FES       : 各演算子のための FESpace（最後のものはテスト関数を指します）
  * action    : 入力（最後の演算子評価を除く）を受け取り、結果をテスト関数評価とドット積を取るように計算するインターフェースのカーネルを持つアクション（アクションが指定されていない場合、全入力ベクトルがテスト関数演算子評価とドット積を取ります）

オプションの引数：

  * regions   : 演算子がアセンブルされるべき領域を指定します。デフォルトの [0] はすべての領域を意味します
  * name      : 印刷メッセージで使用されるこの LinearForm の名前
  * AT        : LinearForm がアセンブルされるグリッドのエンティティを指定します（デフォルト：ON_CELLS）
