```
sigma(spec::Spectrum, specs::AbstractArray{<:Spectrum}, chs::AbstractRange{<:Integer})::Vector{Float64}
```

Computes on a channel-by-channel basis how much `spec` spectrum deviates from the mean of the other spectra in `specs`.  The result is expressed in terms of the standard deviation expected from count statistics alone.   Assuming `spec` varies only by count statistics we expect the result values have a mean 0.0 and a standard deviation of 1.0. 
