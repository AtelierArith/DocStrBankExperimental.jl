```
BDCP(Fields...)
```

Benders-dualカッティングプレーン（BDCP）アルゴリズムのインスタンスを作成します（`Ref.1`）。

# フィールド

  * `MPsolver::Module = HiGHS`: マスタープロブレム（`MP`）のソルバー。`Sy`のタイプに基づいて選択する必要があります。一般的に、`Sy`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーであるべきです。
  * `SP1solver::Module = HiGHS`: KKT条件に基づく再定式化（Bi/Tri-Equivalent I）形式のサブプロブレムのソルバー（`SP1`）。`SP1`はビッグM法に基づく線形化された再定式化であるため、`U`が単なる多面体不確実性集合である場合、少なくともMILPソルバーである必要があります。
  * `SP2solver::Module = Ipopt`: 強双対性に基づく再定式化形式のサブプロブレムのソルバー（`SP2`）。この関数は常に最初に`SP1`を解こうとし、失敗した場合は`SP2`に進みます。`U`が多面体である場合、`SP2`は少なくとも二次元最適化問題であるため、これに特化したソルバー、またはおおよそ非凸二次プログラム（QP）をサポートするソルバーが必要です。
  * `SP2solver_max_iter::Integer = 10000`: `SP2solver`が`SP2`を解くための最大反復回数の制限。
  * `ϵ::Real = 1e-5`: （ネストされた）C&CG法の全体的な絶対停止基準。内部の二次プログラミングソルバーがアクティブな場合、それの許容誤差でもあります。
  * `BigM::Real = 1e5`: `SP1`のビッグM法に基づく線形化された再定式化におけるビッグM値。ビッグMに対して厳密な境界が解析的に得られる場合、アルゴリズムのパフォーマンスが向上することに注意してください。
  * `verbose::Bool = true`: 解決プロセスの詳細出力を制御するスイッチ。

# 参考文献

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
