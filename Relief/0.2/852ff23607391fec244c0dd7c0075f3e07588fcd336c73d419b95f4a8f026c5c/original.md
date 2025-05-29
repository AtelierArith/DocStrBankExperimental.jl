```
multisurf(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
          dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
          f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using MultiSURF algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Ryan Urbanowicz, Randal Olson, Peter Schmitt, Melissa Meeker, and

Jason Moore. Benchmarking Relief-based feature selection methods for bioinformatics data mining. Journal of Biomedical Informatics, 85, 2018.
