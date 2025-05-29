```
surf(data::Array{<:Real,2}, target::Array{<:Integer,1}, m::Signed=-1, 
     dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
     f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using SURF algorithm. The f_type argument specifies whether the features are continuous or discrete  and can either have the value of "continuous" or "discrete".

---

# Reference:

  * Casey S. Greene, Nadia M. Penrod, Jeff Kiralis, and Jason H. Moore.

Spatially uniform ReliefF (SURF) for computationally-efficient filtering of gene-gene interactions. BioData mining, 2(1):5–5, Sep 2009.
