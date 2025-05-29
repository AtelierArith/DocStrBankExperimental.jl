```
qkf(data::QKData{T1,N}, model::QKModel{T,T2}) where {T1<:Real, T<:Real, T2<:Real, N}
```

This function offers a backwards-compatible interface to the Quadratic Kalman Filter (QKF) by accepting the data and model arguments in a reversed order compared to the standard interface. Typically, the preferred order is to pass the model first followed by the data. This method ensures that legacy code that follows the old argument order still functions correctly.

Parameters:

  * data::QKData{T1,N}: An instance containing the observed time series data formatted for the QKF. The data structure organizes the measurements and any associated time indices to be processed by the filter.
  * model::QKModel{T,T2}: An instance containing the model specifications which include the system dynamics, the augmented state representation, and all relevant parameters required to perform the filtering and smoothing operations.

Returns:

  * QKFOutput{T}: A composite output object that includes both the filtering results and the smoothed state estimates. This output encapsulates all intermediate steps and final results computed by invoking the standard qkf function with the proper argument order.

Note:    This reversed argument order function is maintained solely for backwards compatibility. Internally, it simply calls    qkf(model, data) to ensure that the original processing logic remains unchanged.
