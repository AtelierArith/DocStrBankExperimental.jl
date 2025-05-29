```
add_lags(y::Vector{Float64}, p::Int64)
```

Given a vector `y` of length `T`, returns a matrix of size `(T-p) x (p+1)` where the first column is `y[p+1:T]`, second column is `y[p:T-1]` and so on.    
