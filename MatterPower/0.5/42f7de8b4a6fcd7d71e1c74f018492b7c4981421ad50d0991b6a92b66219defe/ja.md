```
t_nowiggle(k, ωm, fbaryon)
```

バリオン音響振動なしの線形物質パワースペクトルの伝達関数（いわゆる*ノーウィグル*伝達関数）。

*参考文献*: Eisenstein and Hu, ApJ, 496, 605 (1998) の式 (29-31)

# 引数

  * `k::Real`: コモービング波数 **の単位は 1/Mpc**。すなわち、波数には **h** は含まれません。
  * `ωm::Real`: 物理バリオン密度パラメータ、`ωm` = Ωm h^2
  * `fbaryon::Real`: バリオン比、`fbaryon` = Ωb/Ωm

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
