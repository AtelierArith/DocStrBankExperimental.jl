```
function reliefseq(data::Array{<:Real, 2}, target::Array{<:Integer, 1}, m::Signed=-1, 
                   k_min::Integer=5, k_max::Integer=10, dist_func::Any=(e1, e2) -> sum(abs.(e1 .- e2), dims=2); 
                   mode::String="discrete", sig::AbstractFloat=1.0, f_type::String="continuous")::Array{Float64,1}
```

Compute feature weights using ReliefSeq algorithm. The mode argument specifies which type of weights update to perform and can either have the value of "k*nearest", "diff" or "exp*rank" (see reference paper). The f*type argument specifies whether the features  are continuous or discrete and can either have the value of "continuous" or "discrete". The sig argument is used when mode has the value of "exp*rank".

---

# Reference:

  * Brett A. McKinney, Bill C. White, Diane E. Grill, Peter W. Li, Ri-

chard B. Kennedy, Gregory A. Poland, and Ann L. Oberg. ReliefSeq: a gene-wise adaptive-k nearest-neighbor feature selection tool for finding gene-gene interactions and main effects in mRNA-Seq gene expression data. PloS ONE, 8(12):e81527–e81527, Dec 2013.
