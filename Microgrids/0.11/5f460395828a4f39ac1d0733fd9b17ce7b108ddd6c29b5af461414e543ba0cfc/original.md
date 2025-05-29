Dispatchable power source (e.g. Diesel generator, Gas turbine, Fuel cell)

# About the types of the fields

All component parameters should be `Float64` except for the *sizing parameter(s)* (here `power_rated`) which type is parametrized as `Topt` and may be also `Float64` or or any another `Real` type (e.g. ForwardDiff's dual number type).
