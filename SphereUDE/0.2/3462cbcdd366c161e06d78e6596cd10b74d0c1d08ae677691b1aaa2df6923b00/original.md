Add Fisher noise to matrix of three dimensional unit vectors

This is carried by the definition of type FisherNoise <: AbstractNoise and extending the base definition +(,) to allow the simple syntax

X*noise = X*noiseless + FisherNoise(kappa=200.)
