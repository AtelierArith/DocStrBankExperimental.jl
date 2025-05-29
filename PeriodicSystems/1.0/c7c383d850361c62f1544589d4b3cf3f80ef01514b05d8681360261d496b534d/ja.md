```
 ps2frls(psysc::PeriodicStateSpace, N) -> sys::DescriptorStateSpace
```

連続時間周期システムの実周波数リフト表現を構築します。

連続時間周期システム `psysc = (A(t),B(t),C(t),D(t))` に対して、実LTI状態空間表現 `sys = (At-Nt,Bt,Ct,Dt)` が構築されます。ここで、`At`、`Bt`、`Ct`、および `Dt` は切り捨てられたブロックToeplitz行列であり、`Nt` はブロック対角行列です。`N` はシステム行列のフーリエ級数における選択された調和成分の数です。

*注:* これは、[ApproxFun.jl](https://github.com/JuliaApproximation/ApproxFun.jl) パッケージにおける周期行列の演算子表現に基づく実験的な実装です。
