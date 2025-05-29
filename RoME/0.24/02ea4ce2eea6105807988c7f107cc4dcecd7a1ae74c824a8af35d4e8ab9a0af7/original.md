```julia
accumulateDiscreteLocalFrame!(mpp, DX, Qc; ...)
accumulateDiscreteLocalFrame!(mpp, DX, Qc, dt; Fk, Gk, Phik)

```

Advance an odometry factor as though integrating an ODE – i.e. $X_2 = X_1 ⊕ ΔX$. Accepts continuous domain process noise density `Qc` which is internally integrated to discrete process noise Qd.  $DX$ is assumed to already be incrementally integrated before this function.  See related `accumulateContinuousLocalFrame!` for fully continuous system propagation.

Notes

  * This update stays in the same reference frame but updates the local vector as though accumulating measurement values over time.
  * Kalman filter would have used for noise propagation: $Pk1 = F*Pk*F' + Qdk$
  * From Chirikjian, Vol.II, 2012, p.35: Jacobian SE(2), Jr = [cθ sθ 0; -sθ cθ 0; 0 0 1] – i.e. dSE2/dX' = SE2([0;0;-θ])
  * `DX = dX/dt*Dt`
  * assumed process noise for `{}^b Qc = {}^b [x;y;yaw] = [fwd; sideways; rotation.rate]`

Dev Notes

  * TODO many operations here can be done in-place.

Related

accumulateContinuousLocalFrame!, accumulateDiscreteReferenceFrame!, [`accumulateFactorMeans`](@ref)
