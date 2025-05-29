```
pretty_print(io::IO, aces_data::ACESData, merit::Merit; projected::Bool = false)
pretty_print(aces_data::ACESData, merit::Merit; projected::Bool = false)
```

Prints the z-scores of the normalised RMS errors of the gate eigenvalue estimator vector for the GLS, WLS, and OLS estimators in `aces_data` using the predictions in the merit data `merit`, or for the projected gate eigenvalue estimator vector if `projected` is `true`.
