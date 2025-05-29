```
predictedarray(r, data::RNAData{T1,T2}, model::AbstractGMmodel) where {T1<:Array, T2<:Array}
```

Calculates the likelihood for multiple histograms and returns an array of PDFs.

# Arguments

  * `r`: The rates.
  * `data::RNAData{T1,T2}`: The RNA data.
  * `model::AbstractGMmodel`: The model.

# Returns

  * `Array{Array{Float64,1},1}`: An array of PDFs for the histograms.
