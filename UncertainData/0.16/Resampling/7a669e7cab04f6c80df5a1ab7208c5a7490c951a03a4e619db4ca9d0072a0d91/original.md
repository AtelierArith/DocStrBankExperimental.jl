resample(uvals::Vector{AbstractUncertainValue}, n::Int) 

Treat `uvals` as a dataset and resample it `n` times.  Returns `n` resampled draws of `uvals`, each being a `length(uvals)`-element vector.  For each returned vector, the i-th element is a unique draw of `uvals[i]`. 
