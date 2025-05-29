```julia
newton(
    br,
    ind_bif;
    normN,
    options,
    start_with_eigen,
    lens2,
    kwargs...
)

```

この関数は、Fold / Hopf点の初期推測を、最小限拡張された定式化に基づいてFold / Hopf問題の解に変換します。

## 引数

  * `br` [continuation](@ref Library-Continuation)への呼び出し後に返される結果
  * `ind_bif` `br`における分岐インデックス

# オプション引数:

  * `options::NewtonPar`、デフォルト値 `br.contparams.newton_options`
  * `normN = norm`
  * `options` この引数を使用して、`br`に保存されているものとは異なるニュートンパラメータを渡すことができます。
  * `bdlinsolver` 制約方程式のための境界付き線形ソルバー
  * `start_with_eigen = false` 最小限拡張された問題を固有要素からの情報で開始するかどうか。
  * `kwargs` 通常のニュートン-クリロフソルバーに渡されるキーワード引数

!!! tip "ODE問題"
    ODE問題の場合、オプション `bdlinsolver = MatrixBLS()`を渡すことで、行列ベースの境界付き線形ソルバーを使用する方が効率的です。


!!! tip "start_with_eigen"
    オプション `start_with_eigen=true`を使用することをお勧めします。

