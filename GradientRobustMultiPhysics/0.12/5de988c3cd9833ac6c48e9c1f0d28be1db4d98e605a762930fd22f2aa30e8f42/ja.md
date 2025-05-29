```julia
BilinearForm(
    operators_linear::Vector{DataType},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action::GradientRobustMultiPhysics.AbstractAction;
    name,
    AT,
    APT,
    apply_action_to,
    factor,
    regions,
    transposed_assembly,
    also_transposed_block,
    transpose_factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

は、以下の引数によって定義されたBilinearFormを生成します：

  * operators_linear  : 2つの線形引数（通常はアンサッツとテスト関数）のための演算子
  * operators_current : 他の未知数のための追加の演算子
  * coeff*from        : operators_currentに使用されるアセンブリ演算子に与えられるPDE未知数IDまたはブロックID
  * action            : 演算子*current+演算子*ansatzの評価（=アクションの入力）をどのように組み合わせてテスト関数演算子で乗算される結果にするかを指示します（アクションが指定されていない場合、全入力ベクトルはテスト関数演算子評価とドット積されます）

オプションの引数：

  * apply*action*to   : 2つの線形引数のうち、アクション入力の一部であるものを指定します（[1] = アンサッツ、[2] = テスト）
  * regions           : 演算子がアセンブルされる領域を指定します。デフォルトの[0]はすべての領域を意味します
  * name              : 印刷メッセージで使用されるこのBilinearFormの名前
  * AT                : BilinearFormがアセンブルされるグリッドのエンティティを指定します（デフォルト：ON_CELLS）
  * APT               : アセンブリに使用されるAPT_BilinearForm AssemblyPatternのサブタイプを指定します（例：ラッピング（wip））
  * factor            : アセンブリ中に乗算される追加の因子
  * transposed_assembly : 結果として得られるアセンブルされた行列を転置します（非対称演算子の場合はここで真と見なします）
  * also*transposed*block : 真の場合、転置されたシステム行列ブロックのアセンブリを切り替えます
  * transpose_factor  : 転置ブロックの因子（デフォルト = factor）
  * store             : 最新のアセンブリ結果を持つBilinearFormの行列を保存します（例：演算子が反復スキームで再アセンブルする必要があるシステムブロックにある場合）

アクションの詳細：アクションは、インターフェース（result, input, ...）を持つカーネル関数と追加の引数情報からなるアクションです。アセンブリ中に、入力は他の未知数の演算子評価（指定されている場合は演算子*current）で埋められ、2つの線形引数のうちの1つの演算子評価（apply*action_toによって決定される）に追加されます。カーネル関数によって計算された結果は、他の線形引数の演算子評価と乗算（ドット積）されます。アクションが指定されていない場合、アセンブリは演算子評価（入力として与えられるはずだったもの）を直接乗算しようとします。
