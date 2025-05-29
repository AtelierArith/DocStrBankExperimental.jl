```
LinearObservationModel(C::AbstractMatrix,D::AbstractMatrix,V::Symmetric)
LinearObservationModel(C::AbstractMatrix,D::AbstractMatrix,V::AbstractMatrix)
LinearObservationModel(C::AbstractMatrix,V::Symmetric)
LinearObservationModel(C::AbstractMatrix,V::AbstractMatrix)
```

Construct linear observation dynamics model with output matrix C, feedthrough matrix D, and symmetric zero-mean measurement noise with symmetric covariance matrix V
