```
 ps2fls(psysc::PeriodicStateSpace, N; P) -> sys::DescriptorStateSpace
```

連続時間周期システムの周波数リフト表現を構築します。

連続時間周期システム `psysc = (A(t),B(t),C(t),D(t))` に対して、(複素) LTI 状態空間表現 `sys = (At-Nt,Bt,Ct,Dt)` が構築されます。ここで、`At`、`Bt`、`Ct` および `Dt` は切り捨てられたブロック Toeplitz 行列であり、`Nt` はブロック対角行列です（[1] または [2] を参照）。 `N` はシステム行列のフーリエ級数における選択された調和成分の数であり、キーワードパラメータ `P` は考慮される完全な周期の数です（デフォルト: `P = 1`）。

*参考文献*

[1] N. M. Wereley. Analysis and control of linear periodically time varying systems.      Ph.D. thesis, Department of Aeronautics and Astronautics, MIT, 1990.

[2] S. Bittanti and P. Colaneri. Periodic Systems : Filtering and Control.     Springer-Verlag London, 2009. 
