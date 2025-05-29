```
l2_hessian(nom_sol)
```

gets hessian according to L2 loss under the assumption that loss(θ₀) = 0. nom*sol is the solution of the nominal ODEProblem.  The Hessian then only requires first derivatives: it is sum*ij dyi/dθ * dyj/dtheta
