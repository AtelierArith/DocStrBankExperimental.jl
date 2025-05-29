```
ConservativePDSProblem(P, u0, tspan, p = NullParameters();
                       p_prototype = nothing,
                       analytic = nothing,
                       std_rhs = nothing)
```

生産-破壊システム（PDS）の形での常微分方程式の保守的なシステムを記述する構造体です。`P`は生産行列$P$を定義する関数を示します。$P$の対角には破壊の対応がない生産項が含まれています。`u0`は初期条件のベクトルで、`tspan`は問題の時間範囲`(t_initial, t_final)`です。オプションの引数`p`は、関数`P`に追加のパラメータを渡すために使用できます。

関数`P`は、署名`production_terms = P(u, p, t)`のアウトオブプレース形式または、インプレース形式`P(production_terms, u, p, t)`で与えることができます。

### キーワード引数:

  * `p_prototype`: `P`がインプレース形式で与えられる場合、`p_prototype`またはそのコピーは`P`の評価を格納するために使用されます。`p_prototype`が明示的に指定されておらず、`P`がインプレースの場合、`p_prototype`は内部的に`zeros(eltype(u0), (length(u0), length(u0)))`に設定されます。
  * `analytic`: PDSの解析解は`f(u0,p,t)`の形で与えられなければなりません。解析解を指定することは、プロットや収束テストに役立ちます。
  * `std_rhs`: アウトオブプレース形式の場合は`du = std_rhs(u, p, t)`として呼び出され、インプレース形式の場合は`std_rhs(du, u, p, t)`として呼び出される標準ODE右辺評価関数です。ODEの生産-破壊表現に依存しないソルバーは、代わりにこの関数を使用して解を計算します。指定されていない場合、`P`を呼び出すデフォルトの実装が使用されます。

## 参考文献

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
