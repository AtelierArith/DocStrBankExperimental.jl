```julia
LinearForm(operator_test::Type{<:??}; ...)
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType};
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64};
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}
LinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action::GradientRobustMultiPhysics.AbstractAction;
    regions,
    name,
    AT,
    factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

次の内容に基づいて（PDE記述レベルの）LinearFormを作成します：

  * operator_test     : テスト関数のための演算子（その部分の線形性を仮定）
  * operators_current : 他の未知数のための追加演算子
  * coeff*from        : assembly*operator!に渡されるPDE未知数IDまたはCurrentSolutionのブロックIDで、operators_currentに使用されるべきもの
  * action            : 入力（最後の演算子評価を除く）を受け取り、テスト関数評価とドット積を計算するインターフェース（result, input, kwargs）を持つAction（アクションが指定されていない場合、全入力ベクトルがテスト関数演算子評価とドット積される）

オプションの引数：

  * regions: 演算子がどの領域でアセンブルされるべきかを指定、デフォルトの[0]はすべての領域を意味する
  * name : 印刷メッセージで使用されるこのLinearFormの名前
  * AT : LinearFormがアセンブルされるグリッドのエンティティを指定（デフォルト: ON_CELLS）
  * factor : アセンブル中に掛け算される追加の因子
  * store : 最新のアセンブル結果を持つLinearFormのベクトルを保存（例：演算子が再アセンブルが必要なシステムブロックにある場合）

アクションの詳細：アクションは、インターフェース（result, input, ...）を持つカーネル関数と追加の引数情報からなるActionです。アセンブル中、入力は他の未知数の演算子評価（すなわちoperators*current）で埋められます。カーネル関数によって計算された結果は、テスト関数の演算子評価（すなわちoperator*test）と掛け算（ドット積）されます。アクションが指定されていない場合、アセンブルは演算子評価（入力として与えられるはずだったもの）を直接掛け算しようとします。
