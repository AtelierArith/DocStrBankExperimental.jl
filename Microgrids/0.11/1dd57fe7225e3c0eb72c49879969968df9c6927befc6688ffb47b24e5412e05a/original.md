Solar photovoltaic generator (including AC/DC converter)

See also `PVInverter` for a variant where the AC/DC converter can be sized as well.

# About the types of the fields

All component parameters should be `Float64` except for the *sizing parameter(s)* (here `power_rated`) which type is parametrized as `Topt` and may be also `Float64` or or any another `Real` type (e.g. ForwardDiff's dual number type).
