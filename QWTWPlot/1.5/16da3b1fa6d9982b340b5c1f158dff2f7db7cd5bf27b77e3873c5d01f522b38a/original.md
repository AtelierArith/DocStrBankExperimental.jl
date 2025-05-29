```
qspectrogram_info(ymin::Float64, ymax::Float64, xmin::Float64, xmax::Float64, z::Matrix{Float64}; p::AbstractArray{Float64, 3} = zeros(1, 1, 1), t::Matrix{Float64} = [0.0 0.0])::Int32
```

parameters:  		

  * xmin minimum x coord
  * xmax maximum x coord
  * ymin minimum y coord
  * ymax maximum y coord
  * z a spectrogramm info. [ny x nx] matrix
  * p a 3D array of points associated with every pixel  [3 x ny x nx] Float64  array
  * tt a parameter (timestamp?) value, assiciated with every pixel [ny x nx] Float64 matrix
