```julia
LinearForm(
    operator::Type{<:??},
    f::GradientRobustMultiPhysics.AbstractUserDataType;
    name,
    kwargs...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, LinearForm, ON_CELLS}

```

は、DataFunctionからL(v) = (f,operator(v))というLinearFormを生成します。

  * operator : テスト関数に適用される演算子
  * action   : DataFunction、評価はテスト関数演算子で乗算されます

オプション引数:

  * regions           : 演算子が組み立てられる領域を指定します。デフォルトの[0]はすべての領域を意味します
  * name              : 印刷メッセージで使用されるこのLinearFormの名前
  * AT                : LinearFormがグリッドのどのエンティティに組み立てられるかを指定します（デフォルト: ON_CELLS）
  * factor            : 組み立て中に乗算される追加の因子
  * store             : 最新の組み立て結果を持つ離散化されたLinearFormのベクトルを保存します
