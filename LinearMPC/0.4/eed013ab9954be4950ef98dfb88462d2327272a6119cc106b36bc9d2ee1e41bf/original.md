```
set_objective!(mpc;Q,R,Rr,S,Qf)
```

Set the weights in the objective function `xN' C' Qf C xN^T + ∑ (C xₖ - rₖ)' Q (C xₖ - rₖ)  + uₖ' R uₖ + Δuₖ' Rr Δuₖ + xₖ' S uₖ

A vector is interpreted as a diagonal matrix.
