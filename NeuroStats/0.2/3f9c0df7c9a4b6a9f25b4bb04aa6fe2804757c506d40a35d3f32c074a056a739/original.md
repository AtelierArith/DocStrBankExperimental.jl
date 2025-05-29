```
dranks(x, nbins)
```

Calculate ranks scaled in 0..nbins.

# Arguments

  * `x::AbstractArray`: some continuous variable, such as reaction time (the time it takes to indicate the response)
  * `nbins::Int64`: number of bins, default is Sturges' formula (`nbins = 1 + log2(length(x)))`)

# Returns

  * `sr::Array{Int64}`
