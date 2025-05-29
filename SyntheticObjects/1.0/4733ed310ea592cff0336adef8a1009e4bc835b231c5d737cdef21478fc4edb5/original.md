```
spokes_object(imgSize = (256, 256), numSpikes = 21, continuous = true, makeRound = true)
```

Generates a 2D or 3D representation of a spokes object.

# Arguments

  * `imgSize::Tuple{Int, Int}`: A tuple of integers representing the size of the image. Default is (256, 256).
  * `numSpikes::Int`: An integer representing the number of spikes. Default is 21.
  * `continuous::Bool`: A boolean indicating whether the spokes are continuous. Default is true.
  * `makeRound::Bool`: A boolean indicating whether the object is round. Default is true.

# Returns

  * `obj2::Array{Float64}`: A 2D or 3D array representing the spokes object.

# Example

```jldoctest
spokes_object((512, 512), 30, false, false)
```
