```
MKLCCG(Fields...)
```

Multiple Kernel Learningを用いた列と制約の生成（MKLCCG）アルゴリズムのインスタンスを作成します（`Ref.1`）。

# フィールド

  * `MPsolver::Module = HiGHS`: マスタープロブレム（`MP`）のソルバー。`Sx`と`Sy`のタイプに基づいて選択する必要があります。一般的に、`Sx`または`Sy`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーであるべきです。
  * `SPsolver::Module = HiGHS`: KKT条件に基づく再定式化形式のサブプロブレム（`SP`）のソルバー（実行可能性オラクルと最適性オラクルの両方）。サブプロブレムオラクルはビッグ-M法に基づく線形化された再定式化であるため、`U`が単に多面体不確実性集合である場合、少なくともMILPソルバーである必要があります。
  * `ϵ::Real = 1e-5`: 拡張CCG法の全体的な絶対停止基準。これは、オラクルの目的値が`ϵ`未満でない場合、現在の`x`が実行不可能であると考える実行可能性オラクルの許容誤差としても使用されます。
  * `BigM::Real = 1e5`: ビッグ-M法に基づく線形化された再定式化における`SP`のビッグ-M値（実行可能性オラクルと最適性オラクルの両方）。ビッグ-Mに対して厳密な上限が解析的に得られる場合、アルゴリズムのパフォーマンスが向上することに注意してください。
  * `verbose::Bool = true`: 解法プロセスの詳細出力を制御するスイッチ。

# 参考文献

1. Han, B. (2024). Multiple kernel learning-aided column-and-constraint generation method.
2. Han, B., Shang, C., & Huang, D. (2021). Multiple kernel learning-aided robust optimization: Learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research, 292(3), 1004-1018.
