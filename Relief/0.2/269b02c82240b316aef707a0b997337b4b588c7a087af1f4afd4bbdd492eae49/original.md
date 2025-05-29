```
swrfstar(data::Array{<:Real,2}, target::Array{<:Integer, 1}, m::Signed=-1, 
              dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
              f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using SWRF* algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Matthew E. Stokes and Shyam Visweswaran.

Application of a spatially-weighted Relief algorithm for ranking genetic predictors of disease. BioData mining, 5(1):20–20, Dec 2012. 23198930[pmid].
