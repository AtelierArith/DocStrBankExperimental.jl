accuracyParams(; [m, σ, reltol]) -> m, σ, reltol

Calculate accuracy parameters m, σ, reltol based on either

  * reltol

or

  * m, σ

TODO: Right now, the oversampling parameter is not taken into account, i.e. σ=2.0 is assumed
