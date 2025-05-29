```
Tn0, xi, et, er = calibLPOE(xin, Tn0in, Ta, q; maxiter=10, λ=1.0)
```

Performs kinematic calibration using the local POE formulation of kinematics.

  * `Tn0` Nominal forward kinematics
  * `xi` Twists
  * `et` Translational errors as function of iteration of algorithm
  * `er` Rotational errors as function of iteration of algorithm
  * `λ` Regularization parameter

See `runtests.jl` for simulated usage. Some functions to generate simulation data for calibration purposes are provided in /home/terasaki/.julia/packages/Robotlib/Cqg2z/src/calibLPOE.jl
