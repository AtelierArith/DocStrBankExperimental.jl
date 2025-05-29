```
polarization_vector(pol::AbstractPolarization, mom::QEDbase.AbstractFourMomentum)
```

Return the polarization vector for a given polarization and four-momentum `mom`. For a definite polarization, the respective `LorentzVector` is returned,  where as for an indefinite polarization, a tuple of polarization vectors is returned.

!!! note "Convention"
    In the current implementation, we use the `base_state` function for `Photon` provided by `QEDcore.jl`.

