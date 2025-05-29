```
boostedsurf(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
            phi::Integer=3, dist_func::Any=(e1, e2, w) -> sum(w.*abs.(e1 .- e2), dims=2); 
            f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using BoostedSURF algorithm.

---

# Reference:

  * Gediminas Bertasius, Delaney Granizo-MacKenzie, Ryan J. Urba-

nowicz, and Jason H. Moore. Boosted spatially uniform ReliefF al- gorithm for genome-wide genetic analysis. Hanover, NH 03755, USA,

2013. Dartmouth College.
