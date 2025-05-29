```
calculate_time_shared_consumption(::AbstractGroupCO, ECModel::AbstractEC; add_EC=true, kwargs...)
```

Calculate the time series of the shared consumed energy for the Cooperative case. In the Cooperative case, there can be shared energy between users, not only self production.

For every time step and user, this time series highlight the quantity of load that is met by using shared energy.

''' Outputs –––- shared*cons*us : DenseAxisArray     Shared consumption for each user and the aggregation and time step '''
