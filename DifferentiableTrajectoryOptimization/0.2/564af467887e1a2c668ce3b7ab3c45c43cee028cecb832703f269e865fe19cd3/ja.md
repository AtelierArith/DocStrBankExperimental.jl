二次計画法 (QP) として問題を扱うソルバーバックエンド

```
QP(y) := argmin_x 0.5 x'Qx + x'(Ry+q)
         s.t.  lb <= Ax + By <= ub
```

# 注意

ここで、問題データタプル `(Q, R, q A, B, lb, ub)` は、制約の線形化と目的の二次化を通じて提供された `ParametricTrajectoryOptimizationProblem` から導出されます。したがって、問題が QP でない場合、この解は正確ではありません！
