```
BlobTracker{T <: AbstractCorrespondence}
```

Example `bt = BlobTracker(sizes=3:5, σw=2.0, σe = 10.0)`

# Optional Keyword arguments:

  * `params::KalmanParams`: Holds the parameters for the kalman filter `σw,σe`
  * `amplitude_th = 0.0001`: blobs must be at least this prominent to be considered
  * `kill_counter_th::Int = 10`: after this many steps without an assigned measurement a blob will die
  * `sizes::AbstractVector`: vector of numbers determining the size scales at which blobs are detected. See docs for [`Images.blob_LoG`](@ref).
  * `preprocessor = ((storage, img)->nothing` a function that processes `img` and stores the result in `storage`
  * `correspondence::AbstractCorrespondence = HungarianCorrespondence(p=1.0, dist_th=2)`: Determines how blobs are assigned to measurements
  * `mask = nothing`: An optional boolean image that is false where you want to ignore blobs and true where you want to track them.
