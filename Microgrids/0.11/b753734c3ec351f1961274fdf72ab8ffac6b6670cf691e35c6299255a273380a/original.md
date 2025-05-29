Battery energy storage (including AC/DC converter)

Battery dynamics is E(k+1) = E(k) − (P(k) + α|P(k)|).Δt where α is a linear loss factor (`loss_factor` field). It relates approximately to the roundtrip efficiency η as η = 1−2α.

# About the types of the fields

All component parameters should be `Float64` except for the *sizing parameter(s)* (here `energy_rated`) which type is parametrized as `Topt` and may be also `Float64` or or any another `Real` type (e.g. ForwardDiff's dual number type).
