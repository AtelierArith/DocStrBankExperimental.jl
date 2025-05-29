```
abstract type VarFeature <: AbstractFeature end
```

Abstract type for feature functions that can be computed on (multi)variate data. Instances of multivariate datasets have values for a number of *variables*, which can be used to define logical features.

For example, with dimensional data (e.g., multivariate time series, digital images and videos), features can be computed as the minimum value for a given variable on a specific interval/rectangle/cuboid (in general, a [`SoleLogics.GeometricalWorld](@ref)).

As an example of a dimensional feature, consider *min[V1]*, which computes the minimum for variable 1 for a given world. `ScalarCondition`s such as *min[V1] >= 10* can be, then, evaluated on worlds.

See also [`scalarlogiset`](@ref), [`featvaltype`](@ref), [`computefeature`](@ref), [`SoleLogics.Interval`](@ref).
