```julia
begin_time_series_update(
    func::Function,
    sys::PowerSystems.System
) -> Any

```

Begin an update of time series. Use this function when adding many time series arrays in order to improve performance.

If an error occurs during the update, changes will be reverted.

Using this function to remove time series is currently not supported.

# Examples

```julia
begin_time_series_update(sys) do
    add_time_series!(sys, component1, time_series1)
    add_time_series!(sys, component2, time_series2)
end
```
