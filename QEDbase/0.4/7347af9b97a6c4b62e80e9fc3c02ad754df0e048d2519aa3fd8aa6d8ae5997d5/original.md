```julia
isonshell(mom, mass)

```

On-shell check of a given four-momentum `mom` w.r.t. a given mass `mass`.

!!! note "Precision"
    For `AbstactFourMomentum`, the element type is fixed to `Float64`, limiting the precision of comparisons between elements. The current implementation has been tested within the boundaries for energy scales `E` with `1e-9 <= E <= 1e5`. In those bounds, the mass error, which is correctly detected as off-shell, is `1e-4` times the mean value of the components, but has at most the value `0.01`, e.g. at the high energy end. The energy scales correspond to `0.5 meV` for the lower bound and `50 GeV` for the upper bound.


!!! todo "FourMomenta with real entries"
      * if `AbstractFourMomentum` is updated to elementtypes `T<:Real`, the `AbstractLorentzVector` should be updated with the `AbstractFourMomentum`.

