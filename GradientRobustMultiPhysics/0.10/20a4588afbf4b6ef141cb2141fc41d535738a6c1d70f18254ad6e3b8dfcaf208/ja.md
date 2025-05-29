```julia
NonlinearForm(
    operator_test::Type{<:??},
    operators_current::Vector{DataType},
    coeff_from::Vector{Int64},
    action_kernel,
    argsizes::Vector{Int64};
    name,
    AT,
    newton,
    sparse_jacobian,
    jacobian,
    dependencies,
    bonus_quadorder,
    store,
    factor,
    regions
) -> GradientRobustMultiPhysics.PDEOperator{Float64, NonlinearForm, ON_CELLS}

```

は、以下の引数によって定義されたNonlinearFormを生成します：

  * operator_test     : テスト関数のための演算子
  * operators_current : 他の未知数のための追加演算子
  * coeff*from        : operators_currentに使用される、assembly*operator!に与えられるPDE未知数IDまたはブロックID
  * action_kernel     : テスト関数演算子と掛け算される非線形量を計算するインターフェースの関数 (result, input, ...)
  * argsizes          : カーネル関数の[result, input]の次元

オプションの引数：

  * dependencies      : カーネル/ヤコビアンの追加依存関係のためのコード文字列（"XTI"の部分文字列）
  * jacobian          : デフォルト = "auto" はForwardDiffによるヤコビアンの自動計算をトリガーします。そうでない場合、ユーザーは次元と依存関係が一致するインターフェースの関数（jacobian, input, ...）を指定できます
  * sparse_jacobian   : ローカルヤコビアンのためにスパース検出とスパース行列を使用しますか？
  * regions           : 演算子が組み立てられるべき領域を指定します。デフォルト[0]はすべての領域を意味します
  * name              : 印刷メッセージで使用されるこのNonlinearFormの名前
  * AT                : NonlinearFormが組み立てられるグリッドのエンティティを指定します（デフォルト：ON_CELLS）
  * factor            : 組み立て中に掛け算される追加の因子
  * store             : 最新の組み立て結果を持つ離散化されたNonlinearFormの行列を保存します
  * bonus_quadorder   : 通常のquadorderに加えて、組み立て時に四分法の次数を適宜増加させます（使用されるFESpacesに基づく）

いくつかの詳細：演算子G(u)が与えられた場合、ニュートン反復はDG u_next = DG u - G(u)を読み取り、これはPDEDescriptionの残りの（線形）演算子に追加されます。これに必要なDGを構築するためのローカルヤコビアン（= 演算子カーネルのヤコビアン）は自動微分（ForwardDiff）によって計算されます。ユーザーは手動でヤコビアンカーネル関数を指定することもでき（これにより組み立て時間が改善される可能性があります）。

デフォルトの依存関係では、演算子とそのヤコビアンのためのカーネル関数はインターフェース

```
function name(result,input,...)
```

を満たす必要があります。ここで、inputは解の演算子のベクトルであり、resultはその後テスト関数のoperator2と掛け算されるもの（またはヤコビアン）です。
