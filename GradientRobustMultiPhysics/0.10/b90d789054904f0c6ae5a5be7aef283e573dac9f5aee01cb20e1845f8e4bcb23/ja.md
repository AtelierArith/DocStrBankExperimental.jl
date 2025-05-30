```julia
LinearForm(
    operator::Type{<:??},
    action::GradientRobustMultiPhysics.AbstractAction;
    name,
    AT,
    regions,
    factor,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

は、アクションから L(v) = (f,operator(v)) という LinearForm を生成します。

  * operator : テスト関数に適用される演算子
  * action   : テスト関数演算子と掛け算される結果を計算するアクション

オプションの引数:

  * regions           : 演算子が組み立てられる領域を指定します。デフォルトの [0] はすべての領域を意味します。
  * name              : 印刷メッセージで使用されるこの LinearForm の名前
  * AT                : LinearForm が組み立てられるグリッドのエンティティを指定します（デフォルト: ON_CELLS）
  * factor            : 組み立て中に掛け算される追加の係数
  * store             : 最新の組み立て結果を持つ離散化された LinearForm のベクトルを保存します。

アクションの詳細: アクションは、インターフェース (result, input, ...) を持つカーネル関数と追加の引数情報からなるアクションです。組み立て中は入力は無視されます（この LinearForms のコンストラクタ内のみ）。カーネル関数によって計算された結果は、テスト関数の演算子評価と掛け算（内積）されます。
