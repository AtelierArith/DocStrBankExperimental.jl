```julia
DiscreteBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{BilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{BilinearForm, Float64, ON_CELLS}

```

(離散)双線形形式のアセンブリパターンを作成します:

  * operators : 対応するFESpaceのために評価されるべき演算子 (最後の2つはアンサッツとテスト関数を指します)
  * FES       : 各演算子のためのFESpace (最後の2つはアンサッツとテスト関数を指します)
  * action    : インターフェースのカーネルを持つアクション (result, input, kwargs) で、入力 (= 最後の演算子評価を除くすべて) を受け取り、結果をテスト関数評価とドット積を取るために計算します (アクションが指定されていない場合、全入力ベクトルがテスト関数演算子評価とドット積を取ります)

オプションの引数:

  * apply*action*to : どちらの2つの線形引数がアクション入力の一部であるかを指定します ([1] = アンサッツ, [2] = テスト)
  * regions   : 演算子がアセンブルされるべき領域を指定します。デフォルトの[0]はすべての領域を意味します
  * name      : 印刷メッセージで使用されるこのLinearFormの名前
  * AT        : LinearFormがアセンブルされるグリッドのエンティティを指定します (デフォルト: ON_CELLS)
