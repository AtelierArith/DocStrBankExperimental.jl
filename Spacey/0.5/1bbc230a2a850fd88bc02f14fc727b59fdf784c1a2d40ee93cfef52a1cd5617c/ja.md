pointgroup_robust(a1, a2, a3)

入力格子に基づいてepsilonを使用してpointGroupを計算します

このルーチンはpointGroup_fastルーチンと似たような方法で動作しますが、有限精度の比較には入力にスケーリングされたepsilonを使用します。epsilonはかなり大きく、入力の最小スケールの10%（変更される可能性があります）です。十分なテストを行うことで、このルーチンはSpaceyパッケージのデファクトスタンダードになるかもしれません。

```
 ```juliadoctest
 julia>  u = [1,0,1e-4]; v = [.5,√3/2,-1e-5]; w = [0,1e-4,√(8/3)];
 julia> pointGroup_robust(u,v,w)
 24-element Array{Array{Float64,2},1}:
 [-1.0 0.0 0.0; -1.0 1.0 0.0; 0.0 0.0 -0.9999999999999999]
 ...
 ```
```
