```
calculate_time_shared_production(::AbstractGroupCO, ECModel::AbstractEC; add_EC=true, kwargs...)
```

Calculate the time series of the shared produced energy for the Cooperative case. In the Cooperative case, there can be shared energy between users, not only self production.

For every time step and user, this time series highlight the quantity of production that meets needs by other users.

''' Outputs –––- shared*prod*us : DenseAxisArray     Shared production for each user and the aggregation and time step '''
