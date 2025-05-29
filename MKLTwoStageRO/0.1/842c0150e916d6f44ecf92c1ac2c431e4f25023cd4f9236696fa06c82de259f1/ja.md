```
CCG(Fields...)
```

(ネストされた)列と制約生成 (C&CG) アルゴリズムのインスタンスを作成します(`Ref.1-2`)。`Sx` が非負の実数値空間である場合、`Ref.1` のアルゴリズム (C&CG) が呼び出されます。`Sx` が非負の混合整数空間である場合、`Ref.2` のアルゴリズム (Nested C&CG) が呼び出されます。

# フィールド

  * `MPsolver::Module = HiGHS`: マスタープロブレム (`MP`) のソルバー。`Sy` と `Sx` のタイプに基づいて選択する必要があります。一般的に、`Sy` または `Sx` が混合整数空間である場合、混合整数線形プログラム (MILP) をサポートするソルバーである必要があります。
  * `SP1solver::Module = HiGHS`: KKT条件に基づく再定式化 (Bi/Tri-Equivalent I) 形式のサブプロブレムのソルバー (`SP1`)。`SP1` はビッグM法に基づく線形化された再定式化であるため、`U` が単なる多面体不確実性集合である場合、そのソルバーは少なくとも MILP ソルバーである必要があります。
  * `SP2solver::Module = Ipopt`: このキーワード引数は、`Sx` が非負の実数値空間である場合にのみ利用可能です。強双対性に基づく再定式化形式 (`SP2`) のサブプロブレムのソルバーです。この関数は常に最初に `SP1` を解こうとし、失敗した場合は `SP2` に進みます。`SP2` は `U` が多面体である場合、少なくとも二次最適化問題であるため、これに特化したソルバー、またはおおよそ非凸二次プログラム (QP) をサポートするソルバーが必要です。
  * `SP2solver_max_iter::Integer = 10000`: このキーワード引数は、`Sx` が非負の実数値空間である場合にのみ利用可能です。`SP2solver` が `SP2` を解くための最大反復回数の制限です。
  * `SP2_MPsolver::Module = Ipopt`: このキーワード引数は、`Sx` が非負の混合整数空間である場合にのみ利用可能です。強双対性に基づく再定式化 (Bi/Tri-Equivalent II) 形式のサブプロブレムのマスタープロブレムのソルバー (`SP2`) です。この関数は常に最初に `SP1` を解こうとし、失敗した場合は `SP2` に進みます。`SP2` のマスタープロブレムは、`U` が単なる多面体不確実性集合である場合でも二次制約を含むため、二次制約付き二次プログラム (QCQP) をサポートする効率的なソルバーが必要です。
  * `SP2_MPsolver_max_iter::Integer = 10000`: このキーワード引数は、`Sx` が非負の混合整数空間である場合にのみ利用可能です。`SP2_MPsolver` が `SP2` のマスタープロブレムを解くための最大反復回数の制限です。
  * `SP2_SPsolver::Module = HiGHS`: このキーワード引数は、`Sx` が非負の混合整数空間である場合にのみ利用可能です。強双対性に基づく再定式化 (Bi/Tri-Equivalent II) 形式のサブプロブレムのサブプロブレムのソルバー (`SP2`) です。この関数は常に最初に `SP1` を解こうとし、失敗した場合は `SP2` に進みます。`SP2` のサブプロブレムのソルバーは `Sx` のタイプにのみ依存するため、`Sx` の混合整数の特徴により、MILP ソルバーである必要があります。
  * `ϵ::Real = 1e-5`: (ネストされた) C&CG メソッドの全体的な絶対停止基準。内部の二次プログラミングソルバーがアクティブな場合、それの許容誤差でもあります。
  * `BigM::Real = 1e5`: ビッグM法に基づく線形化された再定式化における `SP1` のビッグM値。ビッグMに対して厳密な境界が解析的に得られる場合、アルゴリズムのパフォーマンスが向上することに注意してください。
  * `verbose::Bool = true`: 解決プロセスの詳細な出力を制御するスイッチです。

# 参考文献

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.
