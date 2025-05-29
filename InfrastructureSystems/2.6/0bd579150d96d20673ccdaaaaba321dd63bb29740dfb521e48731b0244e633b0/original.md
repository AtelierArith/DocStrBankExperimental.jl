```julia
is_concave(
    pwl::InfrastructureSystems.PiecewiseLinearData
) -> Bool

```

Returns True/False depending on the concavity of the underlying data. For piecewise linear data, it checks if the sequence of slopes is non-increasing.
