```
MethodOfSteps(alg; constrained = false, fpsolve = NLFunctional())
```

遅延微分方程をステップ法で解くアルゴリズムを構築します。ここで、`alg`は計算ステップの基礎となるOrdinaryDiffEq.jlのODEアルゴリズムです。

アルゴリズムが`constrained`の場合、最小遅延を超えないステップサイズのみが取られます。制約がない場合、最小遅延を超えるステップサイズには固定点反復`fpsolve`が適用されます。

引用:

一般的なアプローチ

ZivariPiran, Hossein, and Wayne H. Enright. "An efficient unified approach for the numerical  solution of delay differential equations." Numerical Algorithms 53.2-3 (2010): 397-417.

状態依存遅延

S. P. Corwin, D. Sarafyan and S. Thompson in "DKLAG6: a code based on continuously imbedded sixth-order Runge-Kutta methods for the solution of state-dependent functional differential equations", Applied Numerical Mathematics, 1997.
