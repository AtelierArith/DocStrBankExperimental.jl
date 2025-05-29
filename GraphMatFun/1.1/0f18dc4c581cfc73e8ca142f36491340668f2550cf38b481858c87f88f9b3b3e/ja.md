```
(iter,resnorm)=opt_gauss_newton!(
    graph,
    objfun,
    discr;
    maxit = 100,
    logger = 0,
    errtype = :abserr,
    stoptol = 1e-6,
    cref = get_all_cref(graph),
    input = :A,
    γ0 = 1.0,
    linlsqr = :backslash,
    droptol = 0,
)
```

ガウス–ニュートンアルゴリズムを適用して非線形最小二乗問題を解決します：`graph`の出力を`objfun`の値にフィットさせ、`discr`の点で行います。

変数`graph`は反復中に変更されます。この関数は、終了した反復`iter`と対応する残差ノルム`resnorm`を返します。

kwargsは次のとおりです：

  * `maxit`は最大反復回数を決定します。`logger`の値が>0の場合、中間結果が印刷されます。
  * `errtype`は測定されるエラータイプを決定します。`adjust_for_errtype!`を参照してください。
  * `stoptol`は対応する停止許容値です。
  * `cref`は、`graph`のどの係数が自由変数と見なされ、最適化されるかを決定する`Vector{Tuple{Symbol,Int}}`です。
  * `input`はグラフの入力ノードに対応するラベルです。
  * ステップサイズは`γ0`でスケーリングできます。
  * `linlsqr`と`droptol`は、内部の線形最小二乗問題がどのように解決されるかを決定します；[`solve_linlsqr!`](@ref)を参照してください。
