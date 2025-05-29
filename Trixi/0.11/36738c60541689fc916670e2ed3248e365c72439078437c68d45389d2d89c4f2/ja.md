```
flux_godunov(u_ll, u_rr, orientation_or_normal_direction,
             equations::LinearizedEulerEquations2D)
```

物理フラックス行列の対角化に基づく線形化されたオイラー方程式のためのアップウィンドフラックス。物理フラックス $Au$ は $A=T \Lambda T^{-1}$ であり、ここで $\Lambda$ は $A$ の固有値を保持する対角行列です。$\Lambda = \Lambda^+ + \Lambda^-$ に分解し、$\Lambda^+$ と $\Lambda^-$ はそれぞれ $A$ の正の固有値と負の固有値を保持する対角行列です。次に、左状態 $u_L$ と右状態 $u_R$ に対して、この関数によって計算される数値フラックスは $A^+ u_L + A^- u_R$ であり、ここで $A^{\pm} = T \Lambda^{\pm} T^{-1}$ です。

フラックス行列の対角化は以下で見つけることができます。

  * R. F. Warming, Richard M. Beam and B. J. Hyett (1975) Diagonalization and simultaneous symmetrization of the gas-dynamic matrices [DOI: 10.1090/S0025-5718-1975-0388967-5](https://doi.org/10.1090/S0025-5718-1975-0388967-5)
