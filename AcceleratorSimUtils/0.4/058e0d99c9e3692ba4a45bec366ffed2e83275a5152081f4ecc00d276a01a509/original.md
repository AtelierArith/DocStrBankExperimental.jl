function gen_pinknoise(     beta::Float64=1.0, size::Int64=2^12, dt::Float64=1.0, f0::Float64=1.0)

Random number generator that has a "pink noise" spectrum with frequency rolloff coefficient `beta`.

## positional parameter:

  * beta             – type:Float64, frequency rolloff coefficient
  * size             – type:Int64, number of points

## keyword parameters:

  * dt               – type:Float64, the difference of between each data, total time = size * dt, unit: s
  * f0               – type:Float64, the spectrum has the shape (f0/f)^(beta), unit: Hz.

Note: The algorithm is based on      "Timmer, J. and Koenig, M.: On generating power law noise. Astron. Astrophys. 300, 707-710 (1995)"
