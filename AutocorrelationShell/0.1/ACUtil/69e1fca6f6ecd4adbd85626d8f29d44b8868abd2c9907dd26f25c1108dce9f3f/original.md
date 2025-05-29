```
makenoisy(x::AbstractArray{<:Number}, rng::MersenneTwister, a::Float64)
```

Adds gaussian white noise to an image.

# Arguments

`x::AbstractArray{<:Number}`: image `rng::MersenneTwister`: random number generator ex) rng = MersenneTwister(123) `a::Float64`: A scaling parameter to adjust level of noise.

# Example

```julia
using AutocorrelationShell, Images, FileIO, Random

# Load test image
img = load("./test/pictures/boat.jpg")
img = Float64.(Gray.(img))

noisy_image = makenoisy(img, MersenneTwister(123), 0.7)
```
