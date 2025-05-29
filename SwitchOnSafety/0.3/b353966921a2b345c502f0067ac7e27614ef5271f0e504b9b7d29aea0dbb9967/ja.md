```
mdependentlift(s::AbstractDiscreteSwitchedSystem, m, forward=true)
```

ハイブリッドシステム `s` の `m`-パス依存リフトを返します [LD06]。対応するオートマトンは次元 `m` のデブリュイングラフです。`forward` が `false` の場合、デブリュイングラフは逆方向に機能します [ELD14]。

[LD06] Lee, J.-W. & Dullerud, G. E. Uniform stabilization of discrete-time switched and Markovian jump linear systems Automatica, Elsevier, 2006, 42, 205-21

[ELD14] Essick, R. and Lee, J.-W. and Dullerud, G. E. Control of linear switched systems with receding horizon modal information IEEE Transactions on Automatic Control, 2014, 59, 2340-2352

[PEDJ16] Philippe, M. and Essick, R. and Dullerud, G. E. and Jungers, R. M. Stability of discrete-time switching systems with constrained switching sequences Automatica, 2016, 72, 242-250
