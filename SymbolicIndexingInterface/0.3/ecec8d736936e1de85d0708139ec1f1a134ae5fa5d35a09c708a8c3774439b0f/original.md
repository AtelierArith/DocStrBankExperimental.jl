```
getp(indp, sym)
```

Return a function that takes an value provider, and returns the value of the parameter `sym`. The value provider has to at least store the values of parameters in the corresponding index provider. Note that `sym` can be an index, symbolic variable, or an array/tuple of the aforementioned.

If `sym` is an array/tuple of parameters, then the returned function can also be used as an in-place getter function. The first argument is the buffer (must be an `AbstractArray`) to which the parameter values should be written, and the second argument is the value provider.

Requires that the value provider implement [`parameter_values`](@ref). This function may not always need to be implemented, and has a default implementation for collections that implement `getindex`.

If the returned function is used on a timeseries object which saves parameter timeseries, it can be used to index said timeseries. The timeseries object must implement [`is_parameter_timeseries`](@ref) and [`get_parameter_timeseries_collection`](@ref). Additionally, the parameter object must implement [`with_updated_parameter_timeseries_values`](@ref).

If `sym` is a timeseries parameter, the function will return the timeseries of the parameter if the value provider is a parameter timeseries object. An additional argument can be provided to the function indicating the specific indexes in the timeseries at which to access the values. If `sym` is an array of parameters, the following cases apply:

  * All parameters are non-timeseries parameters: The function returns the value of each parameter.
  * All parameters are timeseries parameters: All the parameters must belong to the same timeseries (otherwise `getp` will error). The function returns the timeseries of all parameter values, and can be accessed at specific indices in the timeseries.
  * A mix of timeseries and non-timeseries parameters: The function can *only* be used on non-timeseries objects and will return the value of each parameter at in the object.
