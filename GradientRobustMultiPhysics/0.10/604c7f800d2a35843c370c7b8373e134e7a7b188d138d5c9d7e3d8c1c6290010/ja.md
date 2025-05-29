```julia
ConvectionOperator(
    a_from::Int64,
    a_operator::Type{<:??},
    xdim::Int64,
    ncomponents::Int64;
    name,
    AT,
    a_to,
    factor,
    ansatz_operator,
    test_operator,
    regions,
    newton,
    store,
    transposed_assembly,
    bonus_quadorder
) -> Union{GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}, GradientRobustMultiPhysics.PDEOperator{Float64, NonlinearForm, ON_CELLS}}

```

は、c(a,u,v) = (a*operator(a)*ansatz*operator(u),test_operator(v))の形の対流項をBilinearForm（またはNonlinearForm、newton引数を参照）として構築します。

  * a_from      : スポットaで使用される登録された未知数のID
  * a_operator  : aに適用される演算子
  * xdim        : 期待される空間次元
  * ncomponents : aの期待される成分数

オプション引数：

  * newton          : c(u,u,v)のニュートン項の組み立てをトリガーするBilinearFormの代わりにNonlinearFormを生成します
  * a*to            : a引数の位置、a*to = 2に設定するとc(u,a,v)の組み立てをトリガーします
  * ansatz_operator : スポットuで使用される演算子（デフォルト：Gradient）
  * test_operator   : スポットvで使用される演算子（デフォルト：Identity）
  * factor          : 組み立て時に掛け算される追加の係数（デフォルト：1）
  * regions         : 演算子が組み立てられるべき領域を指定します。デフォルト[0]はすべての領域を意味します
  * name            : 印刷メッセージで使用されるこの演算子の名前
  * AT              : 演算子が組み立てられるグリッドのエンティティを指定します（デフォルト：ON_CELLS）
  * store           : 最新の組み立て結果を持つ演算子の行列を保存します
