resample_elwise(uvals::Vector{AbstractUncertainValue}, n::Int) 

Resample each element in `uvals` `n` times. The i-th entry in the returned  vector is a `n`-element vector consisting of `n` unique draws of `uvals[i]`.
