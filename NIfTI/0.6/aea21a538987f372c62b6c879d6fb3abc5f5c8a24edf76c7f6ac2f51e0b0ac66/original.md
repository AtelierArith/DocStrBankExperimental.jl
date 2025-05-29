```
NIVolume{T<:Number,N,R} <: AbstractArray{T,N}
```

An `N`-dimensional NIfTI volume, with raw data of type  `R`. Note that if `R <: Number`, it will be converted to `Float32`. Additionally, the header is automatically updated to be consistent with the raw volume. 

# Members

  * `header`: a `NIfTIHeader`
  * `extensions`: a Vector of `NIfTIExtension`s
  * `raw`: Raw data of type `R`
