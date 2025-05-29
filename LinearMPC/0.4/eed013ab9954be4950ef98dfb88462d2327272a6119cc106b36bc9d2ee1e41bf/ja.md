```
set_objective!(mpc;Q,R,Rr,S,Qf)
```

目的関数の重みを設定します `xN' C' Qf C xN^T + ∑ (C xₖ - rₖ)' Q (C xₖ - rₖ)  + uₖ' R uₖ + Δuₖ' Rr Δuₖ + xₖ' S uₖ

ベクトルは対角行列として解釈されます。 ```
